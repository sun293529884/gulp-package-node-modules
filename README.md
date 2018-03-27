# 背景

因小程序开发本身不支持`npm`包管理的开发模式, 同时又希望使用这种开发模式.
又因每一个js文件需要保持小程序规定的代码定义, 所以不能将开发源码直接全部打包.

因此需要将代码中使用的`npm`包复制到项目中（因小程序对项目大小有控制，故将指定`npm`包打包成一个文件至小程序项目）以便再次 `require`


# 使用

```bash
$ npm i gulp-package-node-modules -S
```

```js
import packageNodeModules from 'gulp-package-node-modules' 

const packageConfig = {
    dev: './src',       // 项目开发目录
    dist: './dist',     // 项目打包目录
    output: './npm',    // node_modules打包后的存放目录
    isLiveUpdate: false // 是否实时更新（不管包是否已复制）
}

gulp.src(`./src/**/*.js`)
    .pipe(packageNodeModules(packageConfig))
    .pipe(gulp.dest('./dist'))
```

