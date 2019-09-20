## HTML5 
1. section 元素  表示页面中的一个内容区块
1. article 元素  表示页面中一块与上下文不相关的独立内容
2. aside  元素  表示article元素内容之外的、与article元素内容相关的辅助信息。
3. header 元素  表示页面中的一个内容区块或整个页面的标题
4. hgroup 元素
5. footer  元素  
6. nav 元素
7. figure 元素
## 面试题:什么是标签语义化
标签语义化的目的在于能够直观的认识标签和属性的用途和作用,即用正确的标签做正确的事情
优势:
1. 即使没有css的情况下,页面也可以很好呈现出内容结构,代码结构
2. 增强用户体验: 例如title,alt等属性可以很好的解释名词和图片
3. 有利于SEO,和搜索引擎建立良好的关系,有助于爬虫
4. 便于团队开发和维护
### 新增form表单类型 和标签
1. email 输入 email格式
2. tel 手机号码
3. url 只能输入url格式
4. number 只能输入数字
5. search 搜索框
6. range 范围 滑动条
7. color 拾色器
8. datetime 时间日期(移动支持)
9. month 月份
10. week 星期
### 新增标签:
1. datalist 数据列表 自动补全
2. meter 规定范围内的数量值
3. progress 
### 新增属性:
1. placeholder  占位符
2. autofocus  获取焦点
3. multiple  文件上传多选或多个邮箱地址
4. autocoplete  自动完成,用于表单元素,也可以用于表单自身(on/off)
5. novalidate 关闭验证,可用于form标签
6. required 必填项
7. pattern 正则表达式 验证表单
8. formaction 主要用于表单内某input 提交地址与form提交不同
### 表单事件
oninput 用户输入内容时触发
oninvalid 验证不通过时触发

### 新增全局属性
1. contentEditable 属性 单独某一个标签的属性 可以使内容能被编辑
2. designMode 属性 (这个在js中进行使用,让页面中所有的元素开启可编辑模式)  让页面所有的标签都可以被编辑
3. hidden 属性
4. tabindex 属性(控制input标签按tab键获取到焦点的顺序)
### 全屏显示
```
box.onclick = function (){
	if(ifFullscreen()){
		//退出全屏必须使用 document的api
		if (document.exitFullscreen) {
			document.exitFullscreen();
		}else if (document.webkitCancelFullScreen) {
			document.webkitCancelFullScreen();
		}else if (document.mozCancelFullScreen) {
			document.mozCancelFullScreen();
		}
	}else{
		// 开启全屏 需要作用到元素上面
		if (box.requestFullscreen) {
			box.requestFullscreen();
		}else if (box.webkitRequestFullscreen) {
			box.webkitRequestFullscreen();
		}else if (box.mozRequestFullscreen) {
			box.mozRequestFullscreen();
		}else{
			alert("sorry,无法全屏");
		}
	}
	
}
// 判断是否是全屏
function ifFullscreen(){
	return document.fullscreen || document.webkitIsFullScreen || document.mozFullScreen || false;
}
```
### 多媒体
```
<audio>
	<source src="素材/小手拍拍.mp3">
	<source src="素材/小手拍拍.wav">
	<source src="素材/小手拍拍.ogg">
</audio>

<video controls>
	<source src="素材/movie.ogg" type="">
	<source src="素材/movie.mp4" type="">
	您的浏览器不支持
</video>
```
### 通过js控制 音视频
1. 属性
  1. currentTime 视频播放的当前进度
  2. duration: 视频的总时间
  3. paused: 视频播放的状态
2. 方法
  1. load() 重新加载/视频元素
    1. 语法: audio | video.load()
    2. 用于在更改来源或其他设置后对音频/视频元素进行更新
  2. play() 播放
  3. pause() 暂停
3. 事件
  1. oncanplay: 事件在用户可以开始播放视频/音频(audio/video) 时触发
  2. ontimeuodate  通过该事件来报告当前的播放进度
  3. onended  播放完时触发
4. 全屏: video.webkitRequestFullScreen()
### DOM扩展元素
1. 获取元素
  1. document.querySelector('selector') 选择选中的第一个
  2. document.querySelectorAll('selector') 选择多个
2. 类名操作
  1. Node.classList.add('class') 添加class
  2. Node.classList.remove('class') 删除
  3. Node.classList.toggle('class') 切换class,有则移除,无则添加
  4. Node.classList.contains('class') 检测是否存在class
3. 自定义属性
  1. 格式:  data-*=""
### Web存储
1. storage 存储: window.sessionStorage  window.localStorage (向本地保存数据有可能在浏览器内存里面，有可能在硬盘上面)
2. window.seeionStorage
3. window.localStorage

区别:不同浏览器无法共享 localStorage 或 sessionStorage 中的信息。相同浏览器的不同页面间可以共享相同的 localStorage（页面属于相同域名和端口），但是不同页面或标签页间无法共享 sessionStorage 的信息。
  * setItem(key,value) 设置存储内容
  * getItem(key) 读取存储内容
  * removeItem(key)  删除键值为key的存储内容
  * clear() 清空所有存储内容
  * key(n) 以索引值来获取对应的键

