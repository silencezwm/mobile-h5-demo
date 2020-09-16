<template>
    <div class="hello">
        <h1>{{msg}}</h1>
        <button @click="nativeScan">扫一扫</button>
        <button @click="nativeTakePhoto">拍照</button>
        <button @click="nativeLocation">获取定位</button>
        <button @click="nativeMic">调用麦克风</button>
        <button @click="nativeSelectPhoto">访问本地图库</button>
    </div>
</template>

<script>

    // AeonFamilyFlutter 名称不能随意变更
    const $Flutter = window.AeonFamilyFlutter;

    // native调用H5的方法
    window.scanCallback = result => {
        // 带参调用native方法
        var data = {'code': '888', 'message': result};
        $Flutter && $Flutter.postMessage(JSON.stringify({method: "callBackSuccess", data: data}));
    };

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        methods: {
            nativeScan: function () {
                // 无参数调用native方法
                alert('扫一扫')
                $Flutter && $Flutter.postMessage(JSON.stringify({method: "scan"}));
            },
            nativeTakePhoto: function () {
                alert('拍照')
                // 有参数调用native方法
                var data = {'code': '888', 'message': '消息体'};
                $Flutter && $Flutter.postMessage(JSON.stringify({method: "takePhoto", data: data}));
            },
            nativeLocation: function () {
                alert('获取定位')
                $Flutter && $Flutter.postMessage(JSON.stringify({method: "location"}));
            },
            nativeMic: function () {
                alert('调用麦克风')
                $Flutter && $Flutter.postMessage(JSON.stringify({method: "mic"}));
            },
            nativeSelectPhoto: function () {
                alert('访问本地图库')
                $Flutter && $Flutter.postMessage(JSON.stringify({method: "selectPhoto"}));
            }
        }
    }


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    a {
        color: #42b983;
    }
</style>
