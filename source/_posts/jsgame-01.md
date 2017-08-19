---
title: jsgame-01
date: 2017-08-19 16:33:37
categories: jsgame
tags: [html,js,game]
---
使用js写一些小游戏 游戏1打砖块
<!--more-->
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
