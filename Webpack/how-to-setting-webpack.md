# Webpack 설정 방법
## npm install
```
$ npm i -g webpack //웹팩 설치
$ npm i -D webpack babel-core babel-preset-latest babel-loader //의존 모듈 설치
```

## webpack.config.js
```
const webpack = require('webpack');  
module.exports = {
  devtool: 'source-map',
  entry: './entry-index.js', //번들러 소스
  output: {
    filename: "bundle.js",
  },
  plugins: [
    new webpack.optimize.UglifyJsPlugin({
      compressor: {
        warnings: false,
      },
    })
  ],
  module: {
    loaders: [{
      test: /\.js$/,
      loader: 'babel-loader',
      exclude: /(node_modules|bower_components)/
    }]
  }
};
```