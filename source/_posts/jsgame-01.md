---
title: jsgame-01
date: 2017-08-19 16:33:37
categories: jsgame
tags: [html,js,game]
---
使用js写一些小游戏 游戏1打砖块
<!--more-->
本系列参考教材是 https://space.bilibili.com/39066904#!/

喜欢的可以顺道关注下他的知乎还是很有收获的

这应该会是一个漫长的修行之路

开始吧

html代码很简单
``` html
<!DOCTYPE html>
<html>

    <head>
        <meta charset="utf-8">
        <title>game1</title>
        <style type="text/css">
            canvas {
                border: 1px solid black;
            }
        </style>
    </head>

    <body>
        <canvas id="canvas" width="400" height="300"></canvas>
    </body>
    <script type="text/javascript" src="game.js"></script>

</html>
```
先实现让一个小方块在按下后会左后移动
``` javascript
    log = console.log.bind(console)
    var canvas = document.getElementById('canvas')
    var ctx = canvas.getContext('2d')
    var img = new Image()
    var x = 150
    var y = 200
    img.src = 'paddle.png'
    img.onload = function() {
        ctx.drawImage(img, x, y)
    }
    window.addEventListener('keydown', function(event) {
        var key = event.key
        if (key == "a") {
            x -= 10
            ctx.clearRect(0, 0, canvas.width, canvas.height)
            ctx.drawImage(img, x, y)
        } else if (key == "d") {
            x += 10
            ctx.clearRect(0, 0, canvas.width, canvas.height)
            ctx.drawImage(img, x, y)
        }
    })
```
然后对代码进行优化 每秒刷新30次使得显示更加平滑 第一次修改如下

这样是不对的 因为没有把左右平移放到 Interval里面所以刷新率并没有改变
``` javascript
window.addEventListener('keydown', function(event) {
    var key = event.key
    if (key == "a") {
        x -= 10
        keydown = true
    } else if (key == "d") {
        x += 10
        keydown = true
    }
})
window.addEventListener('keyup', function(event) {
    if (event.key == "a" || event.key == "d") {
        keydown = false
    }
})
setInterval(function() {
    if (keydown == true) {
        ctx.clearRect(0, 0, canvas.width, canvas.height)
        ctx.drawImage(img, x, y)
    }
}, 1000 / 30) //1000 1秒 一秒钟刷新30张
```
再次修改后正确
``` javascript
log = console.log.bind(console)
var canvas = document.getElementById('canvas')
var ctx = canvas.getContext('2d')
var img = new Image()
var x = 150
var y = 200
var rightdown = false
var leftdown = false
img.src = 'paddle.png'
img.onload = function() {
    ctx.drawImage(img, x, y)
}
window.addEventListener('keydown', function(event) {
    var key = event.key
    if (key == "a") {
        rightdown = true
    } else if (key == "d") {
        leftdown = true
    }
})
window.addEventListener('keyup', function(event) {
    if (event.key == "a" || event.key == "d") {
        rightdown = false
        leftdown = false
    }
})
setInterval(function() {
    if (rightdown == true) {
        x -= 10
    } else if (leftdown == true) {
        x += 10
    }
    ctx.clearRect(0, 0, canvas.width, canvas.height)
    ctx.drawImage(img, x, y)
}, 1000 / 30) //1000 1秒 一秒钟刷新30张
```
然后就得到了一个0分代码 修改修改如下

需要对外只暴露函数作为接口

首先抽取滑块作为Paddle对象
``` javascript
imgFromPath = function(src) {
    var img = new Image()
    img.src = src
    return img
}
//滑块类
class Paddle {
    constructor(img, x, y, speed) {
        this.img = imgFromPath(img)
        this.x = x
        this.y = y
        this.speed = speed
    }
    moveRight() {
        this.x -= this.speed
    }
    moveLeft() {
        this.x += this.speed
    }
    getX() {
        return this.x
    }
    getY() {
        return this.y
    }
}
var __main = function() {
    log = console.log.bind(console)
    var canvas = document.getElementById('canvas')
    var ctx = canvas.getContext('2d')
    var rightdown = false
    var leftdown = false

    var paddle = new Paddle('paddle.png', 150, 200, 5)

    window.addEventListener('keydown', function(event) {
        var key = event.key
        if (key == "a") {
            rightdown = true
        } else if (key == "d") {
            leftdown = true
        }
    })
    window.addEventListener('keyup', function(event) {
        if (event.key == "a") {
            rightdown = false
        } else if (event.key == "d") {
            leftdown = false
        }
    })
    setInterval(function() {
        if (rightdown == true) {
            paddle.moveRight()
        } else if (leftdown == true) {
            paddle.moveLeft()
        }
        //清屏
        ctx.clearRect(0, 0, canvas.width, canvas.height)
        //重新画图
        ctx.drawImage(paddle.img, paddle.x, paddle.y)
    }, 1000 / 30) //1000 1秒 一秒钟刷新30张
}
__main()
```
然后继续收取 将整个canvas的绘图 作为对象Engine 把整个画图擦图都封装起来

修改如下
``` javascript
log = console.log.bind(console)
imgFromPath = function(src) {
    var img = new Image()
    img.src = src
    return img
}
class Engine {
    constructor() {
        this.canvas = document.getElementById('canvas')
        this.ctx = canvas.getContext('2d')
        this.keydowns = {}
        this.actions = {}
    }
    init(paddle) {
        var t = this
        setInterval(function() {
            var actions = Object.keys(t.actions)
            for (var i = 0; i < actions.length; i++) {
                var key = actions[i]
                log("key" + key)
                log("keydown:" + t.keydowns[key])
                if (t.keydowns[key]) {
                    log(t.keydowns[key])
                    log("t.actions:" + t.actions[key]())
                    t.actions[key]()
                }
            }
            t.clear()
            t.draw(paddle)
        }, 1000 / 30)
    }
    registerAction(paddle) {
        var t = this

        window.addEventListener('keyup', function(event) {
            t.keydowns[event.key] = false
        })
        window.addEventListener('keydown', function(event) {
            t.keydowns[event.key] = true
            alert(event.key + "+" + t.keydowns[event.key])

        })
        this.actions['a'] = function() {
            paddle.moveLeft()
        }
        this.actions['d'] = function() {
            paddle.moveRight()
        }
        // this.actions[key] = callback()


    }
    update() {}
    //在canvas中画出需要的物体
    draw(o) {
        this.ctx.drawImage(o.img, o.x, o.y)
    }
    clear() {
        this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height)
    }

}
//滑块类
class Paddle {
    constructor(img, x, y, speed) {
        this.img = imgFromPath(img)
        this.x = x
        this.y = y
        this.speed = speed
    }
    moveRight() {
        this.x -= this.speed
    }
    moveLeft() {
        this.x += this.speed
    }
    getX() {
        return this.x
    }
    getY() {
        return this.y
    }
}
var __main = function() {
    var g = new Engine()
    var paddle = new Paddle('paddle.png', 150, 200, 5)

    // g.registerAction('a', function() {
    //     paddle.moveLeft()
    // })
    // g.registerAction('d', function() {
    //     paddle.moveRight()
    // })
    g.registerAction(paddle)
    g.init(paddle)

}
__main()
```
有个很严重的问题一开始按键就会停不下来
这个会在之后再回来改 先照着gua的方法来写 把整个过程封装在了一个function Game中
``` javascript
log = console.log.bind(console)
imgFromPath = function(src) {
    var img = new Image()
    img.src = src
    return img
}
var Game = function() {
    var g = {
        actions: {},
        keydowns: {}
    }
    var canvas = document.getElementById('canvas')
    var context = canvas.getContext('2d')
    g.canvas = canvas
    g.context = context
    g.drawImage = function(img) {
        g.context.drawImage(img.img, img.x, img.y)
    }
    g.clear = function() {
        g.context.clearRect(0, 0, g.canvas.width, g.canvas.height)
    }
    g.registerAction = function(key, callback) {
        g.actions[key] = callback
    }
    window.addEventListener('keydown', function(event) {
        g.keydowns[event.key] = true
    })
    window.addEventListener('keyup', function() {
        g.keydowns[event.key] = false
    })

    setInterval(function() {
        var actions = Object.keys(g.actions)
        for (var i = 0; i < actions.length; i++) {
            var key = actions[i]
            if (g.keydowns[key]) {
                g.actions[key]()
            }
        }
        g.clear()
        g.draw()
    }, 1000 / 30)
    return g
}
//滑块类
class Paddle {
    constructor(img, x, y, speed) {
        this.img = imgFromPath(img)
        this.x = x
        this.y = y
        this.speed = speed
    }
    moveRight() {
        this.x -= this.speed
    }
    moveLeft() {
        this.x += this.speed
    }
    getX() {
        return this.x
    }
    getY() {
        return this.y
    }
}
var __main = function() {
    var g = Game()
    var paddle = new Paddle('paddle.png', 150, 200, 5)

    g.registerAction('a', function() {
        paddle.moveLeft()
    })
    g.registerAction('d', function() {
        paddle.moveRight()
    })
    // g.registerAction(paddle)

    g.draw = function() {
        g.drawImage(paddle)
    }
}
__main()

```
加上一个球 点击f球会发射 碰到墙会反弹
``` javascript
log = console.log.bind(console)
imgFromPath = function(src) {
    var img = new Image()
    img.src = src
    return img
}
var Game = function() {
    var g = {
        actions: {},
        keydowns: {}
    }
    var canvas = document.getElementById('canvas')
    var context = canvas.getContext('2d')
    g.canvas = canvas
    g.context = context
    g.drawImage = function(img, width = img.img.width, height = img.img.height) {
        g.context.drawImage(img.img, img.x, img.y, width, height)
    }
    g.clear = function() {
        g.context.clearRect(0, 0, g.canvas.width, g.canvas.height)
    }
    g.registerAction = function(key, callback) {
        g.actions[key] = callback
    }
    window.addEventListener('keydown', function(event) {
        g.keydowns[event.key] = true
    })
    window.addEventListener('keyup', function() {
        g.keydowns[event.key] = false
    })

    setInterval(function() {
        var actions = Object.keys(g.actions)
        for (var i = 0; i < actions.length; i++) {
            var key = actions[i]
            if (g.keydowns[key]) {
                g.actions[key]()
            }
        }
        g.clear()
        g.update()
        g.draw()
    }, 1000 / 30)
    return g
}
//滑块类
class Paddle {
    constructor(img, x, y, speed) {
        this.img = imgFromPath(img)
        this.x = x
        this.y = y
        this.speed = speed
    }
    moveRight() {
        this.x -= this.speed
    }
    moveLeft() {
        this.x += this.speed
    }
    getX() {
        return this.x
    }
    getY() {
        return this.y
    }
}
//ball
class Ball {
    constructor(img, x, y, speed) {
        this.img = imgFromPath(img)
        this.x = x
        this.y = y
        this.Xspeed = speed
        this.Yspeed = speed
        this.fired = false
    }

    move() {
        if (this.fired) {
            log(this.x)
            log(this.y)
            if (this.x < 0 || this.x > 400) {
                this.Xspeed = -this.Xspeed
            }
            if (this.y < 0 || this.y > 300) {
                this.Yspeed = -this.Yspeed
            }
            this.x += this.Xspeed
            this.y += this.Yspeed
        }
    }
    fire() {
        this.fired = true
    }
    getX() {
        return this.x
    }
    getY() {
        return this.y
    }
}
var __main = function() {
    var g = Game()
    var paddle = new Paddle('paddle.png', 150, 200, 5)
    var ball = new Ball('ball.png', 150, 200, -5)
    g.registerAction('a', function() {
        paddle.moveLeft()
    })
    g.registerAction('d', function() {
        paddle.moveRight()
    })
    g.registerAction('f', function() {
        ball.fire()
    })
    g.update = function() {
        ball.move()
    }
    g.draw = function() {
        g.drawImage(paddle)
        g.drawImage(ball, 50, 50)
    }
}
__main()
```
加入了与板子的碰撞基本实现功能 还有一些小bug和功能下次再改
``` javascript
log = console.log.bind(console)
imgFromPath = function(src) {
    var img = new Image()
    img.src = src
    return img
}
var Game = function() {
    var g = {
        actions: {},
        keydowns: {}
    }
    var canvas = document.getElementById('canvas')
    var context = canvas.getContext('2d')
    g.canvas = canvas
    g.context = context
    g.drawImage = function(img, width = img.img.width, height = img.img.height) {
        g.context.drawImage(img.img, img.x, img.y, width, height)
    }
    g.clear = function() {
        g.context.clearRect(0, 0, g.canvas.width, g.canvas.height)
    }
    g.registerAction = function(key, callback) {
        g.actions[key] = callback
    }
    window.addEventListener('keydown', function(event) {
        g.keydowns[event.key] = true
    })
    window.addEventListener('keyup', function() {
        g.keydowns[event.key] = false
    })

    setInterval(function() {
        var actions = Object.keys(g.actions)
        for (var i = 0; i < actions.length; i++) {
            var key = actions[i]
            if (g.keydowns[key]) {
                g.actions[key]()
            }
        }
        g.clear()
        g.update()
        g.draw()
    }, 1000 / 30)
    return g
}
//滑块类
class Paddle {
    constructor(img, x, y, speed) {
        this.img = imgFromPath(img)
        this.x = x
        this.y = y
        this.speed = speed
    }
    moveRight() {
        this.x -= this.speed
    }
    moveLeft() {
        this.x += this.speed
    }
    collide(ball) {
        if (ball.y + 50 > this.y) {
            if (ball.x > this.x && ball.x < this.x + this.img.width) {
                return true
            }
        }
        return false
    }
    getX() {
        return this.x
    }
    getY() {
        return this.y
    }
}
//ball
class Ball {
    constructor(img, x, y, speedX, speedY) {
        this.img = imgFromPath(img)
        this.x = x
        this.y = y
        this.speedX = speedX
        this.speedY = speedY
        this.fired = false
    }

    move() {
        if (this.fired) {
            log(this.x)
            log(this.y)
            if (this.x < 0 || this.x > 400) {
                this.speedX = -this.speedX
            }
            if (this.y < 0 || this.y > 300) {
                this.speedY = -this.speedY
            }
            this.x += this.speedX
            this.y += this.speedY
        }
    }
    fire() {
        this.fired = true
    }
    getX() {
        return this.x
    }
    getY() {
        return this.y
    }
}
var __main = function() {
    var g = Game()
    var paddle = new Paddle('paddle.png', 150, 200, 5)
    var ball = new Ball('ball.png', 250, 150, -5, -5)
    g.registerAction('a', function() {
        paddle.moveLeft()
    })
    g.registerAction('d', function() {
        paddle.moveRight()
    })
    g.registerAction('f', function() {
        ball.fire()
    })
    g.update = function() {
        ball.move()
        if (paddle.collide(ball)) {
            ball.speedY *= -1
        }
    }
    g.draw = function() {
        g.drawImage(paddle)
        g.drawImage(ball, 50, 50)
    }
}
__main()
```
延时效果(截图只有8帧实际会流畅很多)
![](http://ou7k0sem6.bkt.clouddn.com/demo1.gif)

加入方块
```javascript
log = console.log.bind(console)
imgFromPath = function(src) {
  var img = new Image()
  img.src = src
  return img
}
screenX = 400
screenY = 300
//判断两个物体是否相撞
pub_collide = function(i, j) {
  //(x,y) (x,y+h)(x+w,y)(x+w,y+h)
  //x  j.x j.x+w j.y j.y+h
  var iheight = i.img.height
  var iwidth = i.img.width
  var jheight = j.img.height
  var jwidth = j.img.width
  var d1x = i.x
  var d1y = i.y
  var d2x = i.x
  var d2y = i.y + iheight
  var d3x = i.x + iwidth
  var d3y = i.y
  var d4x = i.x + iwidth
  var d4y = i.y + iheight
  // alert("!!!d1x " + d1x + " d1y " + d1y + " d4x " + d4x + " d4y " + d4y + " j.x " + j.x + " j.width " + j.width + " j.y " + j.y + " j.height " + j.height)
  var result = 0
  if ((d1x < j.x + jwidth && d1x > j.x) && (d1y < j.y + jheight && d1y > j.y)) {
    result += 1
  }
  if ((d2x < j.x + jwidth && d2x > j.x) && (d2y < j.y + jheight && d2y > j.y)) {
    result += 1
  }
  if ((d3x < j.x + jwidth && d3x > j.x) && (d3y < j.y + jheight && d3y > j.y)) {
    result += 1
  }
  if ((d4x < j.x + jwidth && d4x > j.x) && (d4y < j.y + jheight && d4y > j.y)) {
    result += 1
  }
  if (result > 1) {
    log("相撞")
    return {"collide": true, "side": false}
  } else if (result == 1) {
    //侧面相撞
    log("侧面相撞")
    return {"collide": true, "side": true}
  } else {
    return {"collide": false, "side": false}
  }
  // alert("相撞!!!" + d1x + "d1y" + d1y + "d4x" + d4x + "d4y" + d4y + "j.x" + j.x + "j.width" + j.width + "j.y" + j.y + "j.height" + j.height)
}
var Game = function() {
  var g = {
    actions: {},
    keydowns: {}
  }
  var canvas = document.getElementById('canvas')
  var context = canvas.getContext('2d')
  g.canvas = canvas
  g.context = context
  g.drawImage = function(img, width = img.img.width, height = img.img.height) {
    g.context.drawImage(img.img, img.x, img.y, width, height)
  }
  g.clear = function() {
    g.context.clearRect(0, 0, g.canvas.width, g.canvas.height)
  }
  g.registerAction = function(key, callback) {
    g.actions[key] = callback
  }
  window.addEventListener('keydown', function(event) {
    g.keydowns[event.key] = true
  })
  window.addEventListener('keyup', function() {
    g.keydowns[event.key] = false
  })

  setInterval(function() {
    var actions = Object.keys(g.actions)
    for (var i = 0; i < actions.length; i++) {
      var key = actions[i]
      if (g.keydowns[key]) {
        g.actions[key]()
      }
    }
    g.clear()
    g.update()
    g.draw()
  }, 1000 / 30)
  return g
}
//滑块类
class Paddle {
  constructor(img, x, y, speed) {
    this.img = imgFromPath(img)
    this.x = x
    this.y = y
    this.speed = speed
  }
  move(x) {
    if (x < 0) {
      x = 0
    }
    if (x > screenX - this.x) {
      x = screenX - this.x
    }
    return x
  }
  moveRight() {
    this.x = this.move(this.x + this.speed)
  }
  moveLeft() {
    this.x = this.move(this.x - this.speed)
  }
  collide(ball) {
    return pub_collide(ball, this)
    // if (ball.y + 50 > this.img.y) {
    //
    //     if (ball.x > this.img.x && ball.x < this.img.x + this.img.width) {
    //         return true
    //     }
    // }
    // return false
  }
  getX() {
    return this.x
  }
  getY() {
    return this.y
  }
}
class Block {
  constructor(img, x, y) {
    this.img = imgFromPath(img)
    this.x = x
    this.y = y
    this.alive = true
  }
  kill() {
    this.alive = false
  }
  collide(ball) {
    return pub_collide(ball, this)
  }
}
//ball
class Ball {
  constructor(img, x, y, speedX, speedY) {
    this.img = imgFromPath(img)
    this.x = x
    this.y = y
    this.speedX = speedX
    this.speedY = speedY
    this.fired = false
  }

  move() {
    if (this.fired) {
      if (this.x < 0 || this.x > screenX) {
        this.speedX = -this.speedX
      }
      if (this.y < 0 || this.y > screenY) {
        this.speedY = -this.speedY
      }
      this.x += this.speedX
      this.y += this.speedY
    }
  }
  fire() {
    this.fired = true
  }
  getX() {
    return this.x
  }
  getY() {
    return this.y
  }
}
var __main = function() {
  var g = Game()
  var paddle = new Paddle('paddle.png', 150, 200, 5)
  var ball = new Ball('ball.png', 250, 150, -5, -5)
  var block = new Block('block.png', 50, 20)
  g.registerAction('a', function() {
    paddle.moveLeft()
  })
  g.registerAction('d', function() {
    paddle.moveRight()
  })
  g.registerAction('f', function() {
    ball.fire()
  })
  g.update = function() {
    ball.move()
    var result = paddle.collide(ball)
    if (result["collide"]) {
      ball.speedY *= -1
      if (result["side"]) {
        ball.speedX *= -1
      }
    }
    result = block.collide(ball)
    if (block.alive && result.collide) {
      ball.speedY *= -1
      block.kill()
      if (result.side) {
        ball.speedX *= -1
      }
    }
  }

  g.draw = function() {
    g.drawImage(paddle)
    g.drawImage(ball, 50, 50)
    log(block.alive)
    if (block.alive) {
      g.drawImage(block)
    }
  }
}
__main()
```
加入暂停
```javascript
log = console.log.bind(console)
imgFromPath = function(src) {
  var img = new Image()
  img.src = src
  return img
}
screenX = 400
screenY = 300
paused = false
//判断两个物体是否相撞
pub_collide = function(i, j) {
  //(x,y) (x,y+h)(x+w,y)(x+w,y+h)
  //x  j.x j.x+w j.y j.y+h
  var iheight = i.img.height
  var iwidth = i.img.width
  var jheight = j.img.height
  var jwidth = j.img.width
  var d1x = i.x
  var d1y = i.y
  var d2x = i.x
  var d2y = i.y + iheight
  var d3x = i.x + iwidth
  var d3y = i.y
  var d4x = i.x + iwidth
  var d4y = i.y + iheight
  // alert("!!!d1x " + d1x + " d1y " + d1y + " d4x " + d4x + " d4y " + d4y + " j.x " + j.x + " j.width " + j.width + " j.y " + j.y + " j.height " + j.height)
  var result = 0
  if ((d1x < j.x + jwidth && d1x > j.x) && (d1y < j.y + jheight && d1y > j.y)) {
    result += 1
  }
  if ((d2x < j.x + jwidth && d2x > j.x) && (d2y < j.y + jheight && d2y > j.y)) {
    result += 1
  }
  if ((d3x < j.x + jwidth && d3x > j.x) && (d3y < j.y + jheight && d3y > j.y)) {
    result += 1
  }
  if ((d4x < j.x + jwidth && d4x > j.x) && (d4y < j.y + jheight && d4y > j.y)) {
    result += 1
  }
  if (result > 1) {
    log("相撞")
    return {"collide": true, "side": false}
  } else if (result == 1) {
    //侧面相撞
    log("侧面相撞")
    return {"collide": true, "side": true}
  } else {
    return {"collide": false, "side": false}
  }
  // alert("相撞!!!" + d1x + "d1y" + d1y + "d4x" + d4x + "d4y" + d4y + "j.x" + j.x + "j.width" + j.width + "j.y" + j.y + "j.height" + j.height)
}
var Game = function() {
  var g = {
    actions: {},
    keydowns: {}
  }
  var canvas = document.getElementById('canvas')
  var context = canvas.getContext('2d')
  g.canvas = canvas
  g.context = context
  g.drawImage = function(img, width = img.img.width, height = img.img.height) {
    g.context.drawImage(img.img, img.x, img.y, width, height)
  }
  g.clear = function() {
    g.context.clearRect(0, 0, g.canvas.width, g.canvas.height)
  }
  g.registerAction = function(key, callback) {
    g.actions[key] = callback
  }
  window.addEventListener('keydown', function(event) {
    g.keydowns[event.key] = true
  })
  window.addEventListener('keyup', function() {
    g.keydowns[event.key] = false
  })

  setInterval(function() {
    var actions = Object.keys(g.actions)
    for (var i = 0; i < actions.length; i++) {
      var key = actions[i]
      if (g.keydowns[key]) {
        g.actions[key]()
      }
    }
    g.clear()
    g.update()
    g.draw()
  }, 1000 / 30)
  return g
}
//滑块类
class Paddle {
  constructor(img, x, y, speed) {
    this.img = imgFromPath(img)
    this.x = x
    this.y = y
    this.speed = speed
  }
  move(x) {
    if (x < 0) {
      x = 0
    }
    if (x > screenX - this.x) {
      x = screenX - this.x
    }
    return x
  }
  moveRight() {
    this.x = this.move(this.x + this.speed)
  }
  moveLeft() {
    this.x = this.move(this.x - this.speed)
  }
  collide(ball) {
    return pub_collide(ball, this)
    // if (ball.y + 50 > this.img.y) {
    //
    //     if (ball.x > this.img.x && ball.x < this.img.x + this.img.width) {
    //         return true
    //     }
    // }
    // return false
  }
  getX() {
    return this.x
  }
  getY() {
    return this.y
  }
}
class Block {
  constructor(img, x, y) {
    this.img = imgFromPath(img)
    this.x = x
    this.y = y
    this.alive = true
  }
  kill() {
    this.alive = false
  }
  collide(ball) {
    return pub_collide(ball, this)
  }
}
//ball
class Ball {
  constructor(img, x, y, speedX, speedY) {
    this.img = imgFromPath(img)
    this.x = x
    this.y = y
    this.speedX = speedX
    this.speedY = speedY
    this.fired = false
  }

  move() {
    if (this.fired) {
      if (this.x < 0 || this.x > screenX) {
        this.speedX = -this.speedX
      }
      if (this.y < 0 || this.y > screenY) {
        this.speedY = -this.speedY
      }
      this.x += this.speedX
      this.y += this.speedY
    }
  }
  fire() {
    this.fired = true
  }
  getX() {
    return this.x
  }
  getY() {
    return this.y
  }
}
var __main = function() {
  var g = Game()
  var paddle = new Paddle('paddle.png', 150, 200, 5)
  var ball = new Ball('ball.png', 250, 150, -5, -5)
  var block = new Block('block.png', 50, 20)
  g.registerAction('a', function() {
    paddle.moveLeft()
  })
  g.registerAction('d', function() {
    paddle.moveRight()
  })
  g.registerAction('f', function() {
    ball.fire()
  })
  window.addEventListener('keydown',function(event){
    if(event.key == 'p'){
      paused = !paused
    }
  })
  g.update = function() {
    if(paused == true){
      return
    }
    ball.move()
    var result = paddle.collide(ball)
    if (result["collide"]) {
      ball.speedY *= -1
      if (result["side"]) {
        ball.speedX *= -1
      }
    }
    result = block.collide(ball)
    if (block.alive && result.collide) {
      ball.speedY *= -1
      block.kill()
      if (result.side) {
        ball.speedX *= -1
      }
    }
  }

  g.draw = function() {
    g.drawImage(paddle)
    g.drawImage(ball, 50, 50)
    log(block.alive)
    if (block.alive) {
      g.drawImage(block)
    }
  }
}
__main()
```
