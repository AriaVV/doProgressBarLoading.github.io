### 前言
最近用到根据文件的加载情况来制作动态进度条

### HTML结构

	<div id="ProgressBarID">
	    <div>
	    </div>
	</div>

### CSS样式

	<style>
        #ProgressBarID {
            width: 80px;
            height: 15px;
            margin-top: 15px;
            border: 1px solid #efefef;
            -webkit-border-radius: 10px;
            -moz-border-radius: 10px;
            border-radius: 10px;
            overflow: hidden;
        }

        #ProgressBarID > div {
            width: 10%;
            height: 15px;
            text-align: center;
            background-color: #00A0E9;
        }
    </style>

### JS代码

	<script src="jquery-1.12.2.min.js"></script>

	<script>
		/* -- 模拟的数据 -- */
	    var num = [10, 20, 60, 70, 80, 90]
		/* -- 使用闭包让函数一直执行 -- */	
	    for (var i = 0; i < num.length; i++) {
	        (function (i) {
	            doProgressBarLoading(num[i]);
	        })(i)
	    };
	
	    /* --进度条-- */
	    function doProgressBarLoading(progress) {
	        if (progress > 100) {
	            progress = 100;
	        }
	        if (progress <= 100) {
	            $("#ProgressBarID > div").animate({
	                width: progress + '%'
	            }, 1000);
	        }
	    };
	</script>

【end】