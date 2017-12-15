 
<!DOCTYPE html>
<html ><head>
	<title>欢迎使用ZeroBlog®</title>
	<meta http-equiv="X-UA-Compatible" content="IE=Edge"><!-- 防止浏览器quirks模式--> 
<meta name="viewport" content="width=device-width,height=device-height,inital-scale=1.0,maximum-scale=1.0,user-scalable=no;">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black">
<meta name="format-detection" content="telephone=no">
 <link rel="shortcut icon" href="/icon/favicon.ico"> 
		
<link href="css/login_static.css" rel="stylesheet" type="text/css"> 
	 <style type="text/css">
	 </style>

</head> 

<body>
<script type="text/javascript">
	
var random = Math.round(Math.random()*6);
window.document.body.style = "background: url('images/bg"+ random +".jpg')  no-repeat  0px  0px; background-size: 1580px auto;";
</script>


 <div id="login_wrap" align="center">

<div class="blog_icon" align="center"> 
 <font color="#FA8B8B">ZeroBlog®</font> 
</div>
		
		<div class="main" align="center">
			
			<div class="login" align="center">
				<div class="top">
					<span class="left"> <img src="images/login_15.gif" width="152" height="22"> </span>
				</div>
  

 <div id="errortips" class="errortips">用户名或密码错误!</div> 
 
				<div class="login_form" align="center">
				<!-- <form id="loginForm" method="post" action="loginCheck" onsubmit="checknull()"> -->	
						<div class="user">
							<input id="userName" name="userName" 
							class="input" type="text" placeholder="账号" maxlength="20">

						</div>
						<br>
						<div class="user">
							<input id="pwd" name="pwd" class="input" 
							type="password" placeholder="密码" maxlength="20">
						</div>
						<div style="width:230px; float: left; margin:15px 0px 1px 0px"><a id="forgot" target="_blank" style="float:right; font-size:14px;color:#a7a9ad;">忘记密码</a><div id="auto_login" text="7天自动登录" value="remember" ng-model="remember" style="cursor:pointer; font-size:14px;color:#a7a9ad; overflow:hidden"><em style="float:left; border: 1px solid #ced0d5; width:13px; height:13px; display:inline-block "></em><span style="float:left;margin-left:10px ">7天自动登录</span> </div></div>
						
	        <button id="submit" type="button" 
	        onclick="check(userName.value,pwd.value)" class="submit">	
		        	 登录
	         </button>

				 <a href="register">
				 <button name="register" type="button">
						注册
				 </button>
				 </a>
				 
				</div> 
			</div>
 
<script src="<%=path %>/js/jquery.js"></script>
  
 <script type="text/javascript" > 
 
document.getElementById("userName").focus(); 

function keyDown()
{ 
	var keycode = event.keyCode; 
	var realkey = String.fromCharCode(event.keyCode);  

	if(keycode==13) 
	{   
		document.getElementById("submit").click();   	
	}   

} 

document.onkeydown = keyDown; 
 
function trim(str)
{
	return str.replace(/(^\s*)|(\s*$)/g);
}
function replace(text)
{ 
	var ret = text.trim(text);
	if( text == null || ret.length <= 0)
	{ 
		return false;
	} 
	else
	{ 
		return ret;
	}
} 

function check(name,pwd)
{  
	if( false == (name = replace(name)))
	{
		//alert("用户名不得为空或空格！");
		$("#errortips").css("visibility","visible"); 
		$("#errortips").text("用户名不得为空或空格！");
		return false;
	} 
	if( false == (pwd = replace(pwd)))
	{
		//alert("密码不得为空或空格！");
		$("#errortips").css("visibility","visible"); 
		$("#errortips").text("密码不得为空或空格！");
		return false;
	}

	var AjaxURL = "loginCheck";        
	$.ajax({
		type: "POST",
		// dataType: "html",
		url: AjaxURL,
		data: "userName="+name+"&pwd="+pwd,
		success: function (result,status) 
		{   
		result = replace(result);

		if( "onexist" == result ) 
		{      
			document.getElementById("errortips").innerHTML="该用户未注册!"; 
			document.getElementById("errortips").style.visibility="visible"; 
		} 
		else if( "wrong" == result )
		{
			document.getElementById("errortips").style.visibility="visible"; 
			document.getElementById("errortips").innerHTML="用户名或密码错误!";
		}
		else
		{  
			////////     强制改变地址栏内容
			window.location.href="/zeroblog/"+result; 
		} 
		},
		error: function(err,data) {     
			document.getElementById("errortips").style.visibility="visible"; 
			document.getElementById("errortips").innerHTML="返回错误!"; 
		} 
	}); 
} 
	 
</script>

		 </div>
  </div>
	
 

<audio src="bgm/淡水海边,first kiss,父与子.mp3" quality="high" style="position:absolute" loop=true autoplay="true" hidden=true ></audio> 
	 

</body>
</html>
