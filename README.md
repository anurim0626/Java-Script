# Java-Script(shopping mall page)


## -자바 스크립트란?-

🚗자바스크립트(JavaScript)는 객체(object) 기반의 스크립트 언어입니다.
HTML로는 웹의 내용을 작성하고, CSS로는 웹을 디자인하며, 자바스크립트로는 웹의 동작을 구현할 수 있습니다.
자바스크립트는 주로 웹 브라우저에서 사용되나, Node.js와 같은 프레임워크를 사용하면 서버 측 프로그래밍에서도 사용할 수 있습니다.
현재 컴퓨터나 스마트폰 등에 포함된 대부분의 웹 브라우저에는 자바스크립트 인터프리터가 내장되어 있습니다.



## -기본 문법-

🚗자바스크립트에서는 선언되지 않은 변수를 사용하려고 하거나 접근하려고 하면 오류가 발생합니다.
![image](https://user-images.githubusercontent.com/102803326/173486813-8518dc38-24c6-4872-a8b2-545199b95402.png)

🚗쉼표(,) 연산자를 이용하여 여러 변수를 동시에 선언하거나 초기화할 수도 있습니다.
![image](https://user-images.githubusercontent.com/102803326/173486866-362bd9e8-05f4-41a9-931e-56aaf06a8283.png)

  단, 선언되지 않은 변수를 초기화할 경우에는 자동으로 선언을 먼저 한 후 초기화를 진행합니다.



## -doble for 문으로 구현되는 html 태그 작성-

![image](https://user-images.githubusercontent.com/102803326/173486494-55cf90a2-a788-42cd-8d7b-e05bbd3e30e7.png)




## -실행결과 화면-

![image](https://user-images.githubusercontent.com/102803326/173486452-e50b261a-7bdb-462f-b219-74aa0fd83e16.png)


## -가위, 바위, 보 게임-


## -코드

![image](https://user-images.githubusercontent.com/102803326/173517763-401f0a5f-2bd1-442b-9060-ed69629208ec.png)

## -실행과정-

![image](https://user-images.githubusercontent.com/102803326/173519883-aeafcaa0-0056-4056-92e2-fe0c615b15b7.png)

✊🖐✌가위, 바위, 보 중 작성

![image](https://user-images.githubusercontent.com/102803326/173520223-62bf163b-2e4a-4d4d-8fe4-dd0d7d3ffe50.png)

# 쇼핑몰 페이지

### 실행 코드

```css
* { margin:0; padding: 0; }
ul, li { list-style: none; }
a { color: #ffffff; text-decoration: none; }

#header {
	width: 100%;
	height: 80px;
	background-color: black;
	color: white;
	text-align: center;
	line-height: 80px;
}
#nav {
	width: 100%;
	height: 40px;
	background-color: #6094ff;
	color: white;
	line-height: 40px;
}
#nav ul li a {
	float: left;
	padding: 0 10px;
}
.section {
	position: fixed;
	width: 100%;
	height: 100%;
	background-color: white;
}
.section p {
	/* width: 800px; */
	padding: 10px;
	/* margin: 0 auto; */
}
.scroll {
	height: 400px;
	overflow-y: auto;
}
.title {
	padding: 30px 0 20px 0;
	text-align: center;
}
.table_line {
	margin: 0 auto;
	overflow-y: auto;
	border: 1px solid black;
}
.table_line th, .table_line td {
	padding: 5px;
	border: 1px solid black;
}
.table_line .center td {
	text-align: center;
}
#footer {
	position: absolute;
	bottom: 0;
	width: 100%;
	height: 30px;
	background-color: blue;
	color: white;
	text-align: center;
	line-height: 30px;
	font-size: 11px;
}
```
```jsp
<%@ page import="DB.DBConnect"%>
<%@ page import="java.sql.*"%>
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%
	String sql="select max(custno) from member_tbl_02";

	Connection conn = DBConnect.getConnection();
	PreparedStatement pstmt = conn.prepareStatement(sql);
	ResultSet rs = pstmt.executeQuery();
	
	rs.next();
	int num = rs.getInt(1)+1;
%>  

<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<link rel="stylesheet" type="text/css" href="css/style.css?abc">
<title>join</title>

<script type="text/javascript">
	function checkValue() {
		if(!document.data.custname.value) {
			alert("회원성명을 입력하세요.");
			data.custname.focus();
			return false;
		} 
		else if(!document.data.phone.value) {
			alert("전화번호를 입력하세요.");
			data.phone.focus();
			return false;
		} 
		else if (!document.data.address.value) {
			alert("주소를 입력하세요.");
			data.address.focus();
			return false;
		} 
		else if (!document.data.joindate.value) {
			alert("가입일자를 입력하세요.");
			data.joindate.focus();
			return false;
		} 
		else if (!document.data.grade.value) {
			alert("고객등급을 입력하세요.");
			data.grade.focus();
			return false;
		}  
		else if (!document.data.city.value) {
			alert("도시코드를 입력하세요.");
			data.city.focus();
			return false;
		}
		return true;
	}
</script>

</head>
<body>
<header>
	  <jsp:include page="layout/header.jsp"></jsp:include>
 </header>

 <nav>
   	 <jsp:include page="layout/nav.jsp"></jsp:include>
 </nav>
		
 <section class="section">
   	 <h2>홈쇼핑 회원 등록</h2><br>

<form name="data" action="join_p.jsp" method="post" onsubmit="return checkValue()">
			<table class="table_line">
				<tr>
					<th>회원번호(자동발생)</th>
					<td><input type="text" name="custno" value="<%= num %>"  readonly ></td>
				</tr>
				<tr>
					<th>회원성명</th>
					<td><input type="text" name="custname" ></td>
				</tr>
				<tr>
					<th>회원전화</th>
					<td><input type="text" name="phone" ></td>
				</tr>
				<tr>
					<th>회원주소</th>
					<td><input type="text" name="address" ></td>
				</tr>
				<tr>
					<th>가입일자</th>
					<td><input type="text" name="joindate" ></td>
				</tr>
				<tr>
					<th>고객등급[A:VIP,B:일반,C:직원]</th>
					<td><input type="text" name="grade" ></td>
				</tr>
				<tr>
					<th>도시코드</th>
					<td><input type="text" name="city" ></td>
				</tr>
				<tr class="center">
					<td  colspan="2" >
						<input type="submit" value="등록">
						<input type="button" value="취소" onclick="location.href='join.jsp'">
						<input type="button" value="조회" onclick="location.href='member_list.jsp'">
				</tr>
			</table>
		</form>	
   	
 </section>
		
<footer>
	<jsp:include page="layout/footer.jsp"></jsp:include>
</footer>

</body>
</html>
```
## -실행화면-

![image](https://user-images.githubusercontent.com/102803326/186063771-b324ea20-67a1-42f6-9ffe-99dc1c96e1b7.png)

![image](https://user-images.githubusercontent.com/102803326/186063834-6304ea9a-79bd-4e72-8090-ed281d42bed8.png)



