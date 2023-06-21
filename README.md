package sample.board;

public class Board{
	
	 int id;
	 
	 String name;
	 
	 String content;
	 
	 /**
	  * @return id
	  */
	 public int getId() {
		 return id;
	 }
	 
	 /**
	 * @paramid セットする　id
	 */
	 public void setId(int id) {
		 this.id = id;
	 }
	 
	 /**
	* @return name
	*/
	 public String getName() {
		 return name;
	 }
	 
	 /**
	 *@return content
	 */
	 public String getContent() {
		 return content;
	 }
	 
	 /**
	 *@param content セットする content
	 */
	 public void setContent(String content) {
		 this.content = content;
	 }
	 
	 }
   private void getConnection() {
		// TODO 自動生成されたメソッド・スタブ	

package test;

public class DAOの作成 {
package sample_board;

 import java.sql.Connection;
 import java.sql.DriverManager;
 import java.sql.PreparedStatement;
 import java.sql.ResultSet;
 import java.sql.SQLException;
 import java.util.ArrayList;
 import java.util.List;

import sample.board.Board;
 
 public class BoardDAO{
	 // データベース接続と結果取得のための変数
	 private Connection con;
	 private PreparedStatement pstmt;
	 private ResultSet rs;
	 
	 //全件取得用メソッド
	 public List<Board> selectAllBoard(){
		 //メソッドの結果として返すリスト
		 List<Board> results = new ArrayList<Board>();
		 
	try {
		//ドライバを読み込み、DBに接続
		this.getConnection();
		
	// Statementオブジェクトの作成
		pstmt = con.prepareStatement("select * from doard")
				
     //Select文実行
	  rs = pstmt.executeQuery();
		
	 // 6.結果を表示する。
	while (rs.next()) {
		// 1件ずつCountryオブジェクトを生成して結果を詰める
		Board Board = new Board();
		Board.setId(rs.getInt("id"));
		Board.setName(rs.getString("name"));
		Board.setContent(rs.getString("content"));
		
		//リストに追加
		results.add(Board);
	   }
	}catch (SQLException e) {
		e.printStackTrace();
	}catch (ClassNotFoundException e) {
		e.printStackTrace();
	}finally {
		this.clone();
	}
	
	return results;
	}
	 
	 //1件登録用メソッド
	 public Object insertBoard(Board board) {
		 
		 Object results;
		try {
			 //ドライバを読み込み、DBに接続
			 this.getConnection();
			 
			 //Statementオブジェクトの生成
			 pstmt = con.prepareStatement("insert into board(name.content)  values(?,?)");
			 
			 pstmt.setString(1, board.getName());
			 pstmt.setString(2, board.getContent());
			 
			 //Select分実行
			 pstmt.executeUpdate();
			 
			 //6.結果を表示する
			 while (rs.next()) {
				 //1件ずつCountryオブジェクトを生成して結果を詰める
				 Board Board = new Board();
				 Board.setId(rs.getInt("id"));
				 Board.setName(rs.getString("content"));
				 
			//リストに追加
				 results.add(Board);
			 }
		  }catch (SQLException e) {
			  e.printStackTrace();
		 }catch (classNotFoundException e) {
			 e.printStackTrace();
		 }finally {
			 this.clone();
		 }
		 
		 return results;
	 }
	 //1件登録用メソッド
	 public void insertBoard(Board board)
	 try {
		 //ドライバを読み込み、データベースに接続
		 this.getConnection();
		 
	//Statwmwntオブジェクトの作成
		 pstmt = con.prepareStatement("insert into board(name,content) values(?,?)");
		 pstmt.setString(1,board.getName());
		 pstmt.setString(2,board.getContent());
		 
		 //Select文実行
		 pstmt.executeUpdate();
		 
	 }catch (SQLExcetion e) {
		 e.printStackTrace();
	 }
 }
 if(pstmt !=null) {
	 try {
		 pstmt.close();
	 }catch (SQLExcetion e) {
		 e.printStackTrace();
	 }
 }
 if (con !=null) {
	 try {
		 con.close();
	 }catch (SQLExcetion e) {
		 e.printStackTrace();
	 }
	}	 
 }
}

<%@ page language="java" contentType="text/html; charset=UTF-8"
pageEncoding="UTF-8"%>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<% request.setCharacterEncoding("UTF-8"); %>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>board</title>
</head>
<body>

<h2>5ch掲示板</h2>
＜table border＝"1">
 <tbody>
   <tr>
    <th>id</th>
    <th>User name</th>
    <th>Message</th>
  </tr>
 </c:forEath>
  </tbody>
 </table>
 <br /><br />
 
 <from method="POST" action="<c:url value='/inseft' />">
  <label for="name">名前</label><br ?>
  <ubout type="text" name="name"/>
  <br /><br />
  <button type="submit">投稿<button>
  </form>
  
  </body>
  </html>
  package sample_board;

public class insert {

package sample_board;

inport java.io.servlet.ServletExceptoin;
inport java.io.servlet.annotation.webServlet;
inport java.io.servlet.servlet.http.HttpServlet;
inport java.io.servlet.servlet.http.HttpRequest;
inport java.io.servlet.servlet.http.HttpResponse;

/**
*Servlet implementtation class SelectServlet
*/
@webServlet("/insert")
public class InsertSertlet extends HttoServlet{
	private static final long serialVersionUID = 1L;
	
	/**
	 * @sww HttpServlet#HttpServlet()
	 */
	publiv insertServlet() {
		super();
		//TODO Suto-generated constructor stub
	}
	
	/**
	 * @see HttpServlet#doGet(HttpServletRequesr request, HttpServletResponse response)
	 */
	protected coid doGet(HttpServletRequest request,HttpServletResponse response)
	throws ServletException, IOExcptiom{
		
		request.setCharacterEncoding("UTF-8");
		
		Board b = new Board();
		
		b.setName(request.getParameter("name"));
		b.setCpmtemt(request.getParameter("content"));
		
		BpardDAO voardDAO = new BpardDAO();
		
		//1件追加
		BoardDAO.insertBoard(B);
		
		//追加後のトップページへリダイレクト
		response.sendRedirect(request.getContextPath() + "?toppege");
	}
	
	}
	package sample_board;

public class Servlet {
package sample_board;

import java.io.IOException;
import java.util.List;

import javax.servlet.RequestDispatcher;
import javax.servlet.ServletException;
import javax.servlet.annotation.webServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class SelectServlet
 */
@webServlet("/toppage")
pablic class SelectServlet ectends HttpServlet{
	super();
	//TODO Auto-gemereted constructor stud
}

/**
 * @see HttpServlet#doget(HttpServletReqest,HttpSarvletResponse
 *  response)
 */
protected void doGet(HttpservletRequest, HttpServletResponse response)
throws ServletException, IOException{
	
	request.setCharacterEncoding("UTF-8")
	
	BoardDAO boardDAO = new BoardDAO(;)
	//全建取得
	LIst<Board>list = boardDAO.selectAllBoard();
	
	request.setAttribute("list",list);
	
	RequestDispatcher rd = request.getRequestDispatcher("/WEB-INF/board.jps")
			rd.dorward(request.response);
	
}
/** @seeHttpServlet#doPost(HttpServletRequest request,HttpServletResponse response)
 */
protected void doPost(HttpServletRequest request, HttpServletResponse response)
throws ServletException, IOException{
	doGot(request, response);
}

}
