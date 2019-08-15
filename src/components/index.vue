<template>
    <div class="container flex-center">
        <div class="card-box">
            <div class="card-item flex-center" @click="showThree">
                0-3岁
            </div>
            <div class="card-item flex-center" @click="isShowSix = true">
                3-6岁
            </div>
        </div>

        <el-dialog title="请答题" :visible.sync="isShowThree" width="50%" center>
            <div>需要注意的是内容是默认不居中的</div>

            <div slot="footer" class="dialog-footer">
                <el-button @click="isShowThree = false">取 消</el-button>
                <el-button type="primary" @click="isShowThree = false">确 定</el-button>
            </div>
        </el-dialog>
    </div>
</template>

<script>
    const fs = require('fs')
    const path = require('path')

    export default {
        name: 'index',
        data() {
            return {
                isShowThree: false,
                isShowSix: false,
            }
        },
        created() {
            this.initData();
        },
        methods: {
            initData() {
                console.log(fs)
                let files = fs.readdirSync(path.resolve(__dirname, '../') + '/assets/images');
                let jsFiles = files.filter(f => {
                    return f.endsWith('.jpg')
                });
                for (let f of jsFiles) {
                    console.log(f);
                    // let filename = '/'.concat(f.replace('.js', '').trim())
                    // let mapping = require(path.resolve(__dirname, '../') + '/router/' + f)
                }
            },
            showThree: function () {
                this.isShowThree = true;
                // 加载题目
            }
        }
    }
</script>

<style scoped lang="scss">
    .container {
        height: 100%;
        background: #333;
        .flex-center {
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .card-box {
            width: 500px;
            height: 500px;
            display: flex;
            justify-content: space-around;
            align-items: center;
            .card-item {
                width: 40%;
                height: 200px;
                cursor: pointer;
                background: #fff;
                border-radius: 5px;
                font-size: 24px;
            }
        }
    }
</style>
