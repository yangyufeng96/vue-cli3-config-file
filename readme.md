## 插件配置

```
const webpack = require('webpack')
const path = require('path');
 
function resolve(dir) {
    return path.join(__dirname, dir)
}
module.exports = {
    // 插件配置
    configureWebpack: {
        plugins: [
            new webpack.ProvidePlugin({
                jQuery: 'jquery',
                $: 'jquery'
            })
        ]
    },
    // 别名
    chainWebpack: config => {
        config.entry.app = ["babel-polyfill", resolve('src/main.js')],
        config.resolve.alias
            .set('@', resolve('src'))
            .set('./@assets', resolve('src/assets'))
            .set('@components', resolve('src/components'))
            .set('@font', resolve('src/font'));
    }
}
