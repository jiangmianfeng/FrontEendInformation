# XML

# 1. 概念

## 1.1. ML（标记语言）  <></>

- 标记语言都是放置在标签之间

- 当下流行的标记语言有两种:HTML和XML
- 它们都有同一个父语言SGML(Standard Generalized Markup Language)发展起来的
- HTML和XML的标准都是由W3C制定的

## 1.2. XML全称  extensible Markup Language,可扩展标签语言

- 时间：于 1998 年 2 月 10 日成为 W3C 的推荐标准

## 1.3. HTML与XML对比

- HTML称为超文本标签语言，X(extensible ) ML扩展标记语言
- HTML的标签都是固定的，而XML的标签都是扩展的
- HTML重点显示页面，而XML重点数据传递的载体或者项目的配置文件
- XML不是HTML替代版，有着各自不同的目的

## 1.4. 解析器

- 神器 : XMLSpy (解析+编码)
- 浏览器
- Eclipse
- Idea

## 1.5. 横向对比

- html

```html
<html>
	<head>
		<title>学生管理</title>	
	</head>
	<body>
		<table border="1" align="center">
			<tr>
				<th>学号</th>
				<th>姓名 </th>
			</tr>
			<tr>
				<td>1001</td>
				<td>张三</td>
			</tr>
			<tr>
				<td>1002</td>
				<td>李四</td>
			</tr>
		</table>	
	
	</body>	
	
</html>
```

- xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<students>
	<student>
		<id>1001</id>
		<name>张三</name>
		<age>18</age>
	</student>
	<student>
		<id>1002</id>
		<name>张三2</name>
		<age>28</age>
	</student>
</students>

```

# 2. XML语法 

第一行是版本和编码格式声明

```xml
<?xml version="1.0" encoding="UTF-8" ?>
```

- 注

  - `<?xml 和 ?> `内容之间不要加上空格 ，属性和值之间用等号，属性和属性之前用空格 

  - XML区分大小写
  - 根目录只能一个
  - 所有的标记都有开闭
  - 如果嵌套要正确嵌套
  - html不认识多个空格，如果有多个空格只能识别一个；XML可以识别多个空格 

# 3. XML组成

## 3.1. 元素 <>

## 3.2. 属性<  xx=xx >

## 3.3. 实体

## 3.4. 注释 :  与THML相同

## 3.5. CDATA : 表示HTML内容：<![ CDATA[] ]>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<students>
	<!-- <student>:元素|标签   id="1001":属性 -->	
	<student id="1001">
		<name>张三</name>
		<age>18</age>
	</student>
	
	<student id="1002">
		<name>李四</name>
		<age>19</age>
	</student>
	
	<student id="1003">
		<!-- 实体 -->	
		<name>&apos;&quot;&amp;&lt;&gt;</name>
		<age>20</age>
	</student>
	
	<student id="1004">
		<!-- CDATA : <![CDATA[]]> -->	
		<name>
			<![CDATA[
				<p>1111<111</p>
				<p>1111<111</p>	
			]]>
		</name>
		<age>21</age>
	</student>
</students>

```

# 4. XML通过样式显示

## 4.1. 使用CSS样式

- main.css

```css
id{
	background-color:#CCC;
}
name{
	background-color:#F40;
}
age{
	background-color:rgba(255,0,0,0.5);
}
```

- xxx.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<?xml-stylesheet type="text/css" href="main.css"?>
<students>
	<student>
		<id>1001</id>
		<name>张三</name>
		<age>18</age>
	</student>
	<student>
		<id>1002</id>
		<name>张     三2</name>
		<age>28</age>
	</student>
</students>
```

## 4.2. 使用XSLT(extensiable stylesheet Language Transformation)显示

- main.xslt

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
	<xsl:template match="/">
		<html>
			<body style="background-color:#ccc">
				<table border="1">
					<xsl:for-each select="students/student">
						<tr>
							<td>
									<xsl:value-of select="id"/>
							</td>
							<td>
									<xsl:value-of select="name"/>
							</td>
							<td>
									<xsl:value-of select="age"/>
							</td>
						</tr>	
					</xsl:for-each>
				</table>
			</body>
		</html>
	</xsl:template>
</xsl:stylesheet>
```

- xxx.xml

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<?xml-stylesheet type="text/xsl" href="main.xslt"?>
<students>
	<student>
		<id>1001</id>
		<name>张三</name>
		<age>18</age>
	</student>
	<student>
		<id>1002</id>
		<name>张     三2</name>
		<age>28</age>
	</student>
</students>
```

# 5.  XML验证

- XML文档

  - 合法的XML=格式良好+验证通过(DTD或Schema)

- 为什么需要验证 : 有些单词有语境(table表示桌子和表格)或命名不一样，就没有标准可言，解析就会很麻烦

  ```xml
  <!-- 命名不一样 -->
  <书籍>
      <计算机书>
      	<书名>Java大神</书名>    
          <价格>5000</价格>
      </计算机书>
  </书籍>
  
  <books>
      <computer>
      	<bookname>Java大神</bookname>
          <priece>5000</priece>
      </computer>
  </books>
  
  <!-- 语境不一样 -->
  <table>
  	<tr>
      	<td></td>
          <td></td>
      </tr>   	 	
  </table>    
  
  <table>
  	<type>长桌</type>
      <meterial>木头</meterial>
  </table>
  ```

## 5.1. DTD验证 ： *.dtd

- main.dtd

  ```dtd
  <?xml version="1.0" encoding="UTF-8"?>
  <!-- 
  	必须列出所有用到的标签，一个都不能少 
  	(id,name,age,gender,address):代表子元素出现顺序
  	* 可有可无可多个 
  	+ 至少有一个
  	ELEMENT 表示是标签类型
  	#PCDATA表示字符串类型
  -->
  <!ELEMENT students (student)>
  <!ELEMENT student (id,name,age,gender*,address+)>
  <!ELEMENT id (#PCDATA)> 
  <!ELEMENT name (#PCDATA)>
  <!ELEMENT age (#PCDATA)>
  <!ELEMENT gender (#PCDATA)>
  <!ELEMENT address (#PCDATA)>
  
  ```

- xxx.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!-- 
	引入DTD验证 : <!DOCTYPE students SYSTEM "main.dtd">
	students 必须根标签名 
	DTD类型
		SYSTEM 小范围 
		PUBLIC 行业共用
	"main.dtd":相对路径 
<!DOCTYPE students SYSTEM "main.dtd">
 -->
<!DOCTYPE students[
	<!ELEMENT students (student)>
	<!ELEMENT student (id,name,age,gender*,address+)>
	<!ELEMENT id (#PCDATA)> 
	<!ELEMENT name (#PCDATA)>
	<!ELEMENT age (#PCDATA)>
	<!ELEMENT gender (#PCDATA)>
	<!ELEMENT address (#PCDATA)>
]>
<students>
	<student>
		<id></id>
		<name></name>
		<age></age>
		<gender></gender>
		<gender></gender>
		<address></address>
		<address></address>
	</student>
</students>
```



- 局限性
  - 标签间值的类型不可指定
  - 标签没有枚举类型
  - 无法设置值的范围
  - 无法限制字符串的长度
  - 无法支持命名空间
  - ....
- 解决上面的局限性，使用 Schema

## 5.2. Schema验证 : *.xsd

- 不带命名空间

- main.xsd

  ```html
  <?xml version="1.0" encoding="UTF-8" ?>
  <!-- 定义一个schema ，
  	xmlns：是自己的命名空间
  	targetNamespace: 别的xml引入我时所指定命名空间
   -->
  <schema xmlns="http://www.w3.org/2001/XMLSchema">
  	<element name="students">
  		<complexType>
  			<!-- 
  				all:所有的都要出现，顺序随意 
  				sequence : 所有的都要出现，顺序有序 
  				choice ：只能选一个(非此即彼) -->
  			<sequence>
  				<element name="student">
  					<complexType>
  						<sequence>
  							<element name="id" type="integer" />
  							<element name="name">
  								<simpleType>
  									<restriction base="string">
  										<minLength value="4"/>		
  										<maxLength value="10" />
  									</restriction>
  								</simpleType>
  							</element>
  							<element name="age">
  								<simpleType>
  									<restriction base="integer">
  										<minInclusive value="1"/>
  										<maxInclusive value="100"/>
  									</restriction>
  								</simpleType>
  							 </element>
  							<element name="gender" type="string" />
  							<element name="address" type="string" />
  						</sequence>
  					</complexType>
  				</element>
  			</sequence>
  		</complexType>
  	</element>
  
  </schema>
  ```

- x.xml

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!-- 没有命名空间只能使用 xsi:noNamespaceSchemaLocation 方式导入-->
  <students xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
   xsi:noNamespaceSchemaLocation="main.xsd">
  	<student>
  		<id>1001</id>
  		<name>1234567890</name>
  		<age>18</age>
  		<gender></gender>
  		<address></address>
  	</student>
  </students>
  
  ```

- 带命名空间

- main2.xsd

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!-- 定义schema
  	 自己有命名空间 xmlns，但没有使用
  	 targetNamespace ： 别的xml引入我时所指向的命名空间
  	 有targetNamespace都要加上elementFormDefault="qualified"
   -->
  <schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="http://www.wanho.net" elementFormDefault="qualified">
  	<element name="students">
  		<complexType>
  			<!-- 
  				all:所有的都要出现，顺序随意 
  				sequence : 所有的都要出现，顺序有序 
  				choice ：只能选一个(非此即彼) -->
  			<sequence>
  				<element name="student">
  					<complexType>
  						<sequence>
  							<element name="id" type="integer"/>
  							<element name="name">
  								<simpleType>
  									<restriction base="string">
  										<minLength value="4"/>
  										<maxLength value="10"/>
  									</restriction>
  								</simpleType>
  							</element>
  							<element name="age">
  								<simpleType>
  									<restriction base="integer">
  										<minInclusive value="1"/>
  										<maxInclusive value="100"/>
  									</restriction>
  								</simpleType>
  							</element>
  							<element name="gender" type="string"/>
  							<element name="address" type="string"/>
  						</sequence>
  					</complexType>
  				</element>
  			</sequence>
  		</complexType>
  	</element>
  </schema>
  
  ```

- x.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!-- xmlns：我的命名空间，我可选择使用，也可选择不使用
xsi:schemaLocation 有命名空间使用此方式导入 
 -->
<wanho:students xmlns:wanho="http://www.wanho.net" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.wanho.net main2.xsd">
	<wanho:student>
		<wanho:id>1001</wanho:id>
		<wanho:name>11111</wanho:name>
		<wanho:age>18</wanho:age>
		<wanho:gender></wanho:gender>
		<wanho:address></wanho:address>
	</wanho:student>
</wanho:students>

```



# 6. Java解析XML 

## 6.1. 四大解析对比

- XML的解析方式分为四种：

- 原生解析

  - 1、DOM解析；

    【优点】

    - 允许应用程序对数据和结构做出更改。

    - 访问是双向的，可以在任何时候在树中上下导航，获取和操作任意部分的数据。

    【缺点】

    - 通常需要加载整个XML文档来构造层次结构，消耗资源大。

  - 2、SAX解析；

    【优势】

    - 不需要等待所有数据都被处理，分析就能立即开始。

    - 只在读取数据时检查数据，不需要保存在内存中。

    - 可以在某个条件得到满足时停止解析，不必解析整个文档。

    - 效率和性能较高，能解析大于系统内存的文档。

    【缺点】

    - 需要应用程序自己负责TAG的处理逻辑（例如维护父/子关系等），文档越复杂程序就越复杂。

    - 单向导航，无法定位文档层次，很难同时访问同一文档的不同部分数据，不支持XPath。

- 第三方解析：依赖第三方jar包

  - 3、JDOM解析；

    - 【优点】

      - 使用具体类而不是接口，简化了DOM的API。

      - 大量使用了Java集合类，方便了Java开发人员。

      【缺点】

      - 没有较好的灵活性。

      - 性能较差。

  - 4、DOM4J解析。

    - 【优点】
      - 大量使用了Java集合类，方便Java开发人员，同时提供一些提高性能的替代方法。
      - 支持XPath。
      - 有很好的性能。

    - 【缺点】
      - 大量使用了接口，API较为复杂。 

## 6.2. xpath语法 

### 6.2.1. 表达式

- 第一种形式
  - /AAA/DDD/BBB：表示一层一层的，AAA下面DDD下面的BBB
- 第二种形式
  - //BBB：表示和这个名称相同，表示只要名称是BBB，都得到
- 第三种形式
  - /*:所有元素
- 第四种形式
  - BBB[1]：　表示第一个BBB元素
  - BBB[last()]：表示最后一个BBB元素
- 第五种形式
  - //BBB[@id]：表示只要BBB元素上面有id属性，都得到
- 第六种形式
  - //BBB[@id='b1']表示元素名称是BBB,在BBB上面有id属性，并且id的属性值是b1
- 例如：
  - /students/student[@id='1002'] 
  - 根students标记下student标记下属性名为id且属性值为1002的student元素

### 6.2.2. dom4j集成xPath操作

- 使用dom4j集成xpath操作

  - 默认的情况下，dom4j不支持xpath，如果想要在dom4j里面是有xpath，引入支持xpath的jar包，如下：

    `jaxen.jar`包

- 在dom4j里面提供了两个方法，用来支持xpath

  - selectNodes("xpath表达式")，获取多个节点
  - selectSingleNode("xpath表达式")，获取一个节点

## 6.3. DOM4j 解析示例

- 加入jar包

  - dom4j-1.6.1.jar
  - jaxen-1.1-beta-7.jar

- 代码

  ```java
  package net.wanho;
  
  import java.io.File;
  import java.io.FileWriter;
  import java.io.IOException;
  import java.util.ArrayList;
  import java.util.List;
  
  import org.dom4j.Document;
  import org.dom4j.DocumentException;
  import org.dom4j.Element;
  import org.dom4j.Node;
  import org.dom4j.io.SAXReader;
  import org.dom4j.io.XMLWriter;
  
  public class Dom4j_Demo {
  
  	public static void main(String[] args) throws DocumentException, IOException {
  		
  		//追回
  		// append();
  		// update();
  		// delete();
  		findAll();
  	}
  	
  	private static void findAll() throws DocumentException, IOException {
  		//load document
  		File file = new File("student.xml");
  		Document document = new SAXReader().read(file);
  		
  		//找到最后一个学生，删除 
  		List<Node> nodes = document.selectNodes("/students/student");
  		List<Student> students = new ArrayList<>();
  		for(Node node:nodes) {
  			
  			int id = Integer.parseInt(node.selectSingleNode("id").getText());
  			String name = node.selectSingleNode("name").getText();
  			int age = Integer.parseInt(node.selectSingleNode("age").getText());
  			Student stu = new Student(id,name,age);
  			students.add(stu);
  		}
  		
  		System.out.println(students);
  		
  	}
  	
  	private static void delete() throws DocumentException, IOException {
  		//load document
  		File file = new File("student.xml");
  		Document document = new SAXReader().read(file);
  		
  		//找到最后一个学生，删除 
  		Node node = document.selectSingleNode("/students/student[last()]");
  		document.getRootElement().remove(node);
  		
  		//save
  		XMLWriter writer =new XMLWriter(new FileWriter(file));
  		writer.write(document);
  		writer.flush();
  		writer.close();
  	}
  	
  	private static void update() throws DocumentException, IOException {
  		//load document
  		File file = new File("student.xml");
  		Document document = new SAXReader().read(file);
  		
  		//找到最后一个学生，修改姓名 
  		Node node = document.selectSingleNode("/students/student[last()]/name");
  		node.setText("王六侠");
  		
  		//save
  		XMLWriter writer =new XMLWriter(new FileWriter(file));
  		writer.write(document);
  		writer.flush();
  		writer.close();
  	}
  
  	private static void append() throws DocumentException, IOException {
  		//load document
  		File file = new File("student.xml");
  		Document document = new SAXReader().read(file);
  		
  		//append
  		Element root = document.getRootElement();
  		Element stuEle= root.addElement("student");
  		
  		Element idEle = stuEle.addElement("id");
  		idEle.setText("1003");
  		
  		Element nameEle = stuEle.addElement("name");
  		nameEle.setText("王五侠");
  		
  		Element ageEle = stuEle.addElement("age");
  		ageEle.setText("30");
  		
  		//save
  		XMLWriter writer =new XMLWriter(new FileWriter(file));
  		writer.write(document);
  		writer.flush();
  		writer.close();
  	}
  }
  ```


# 7. 练习

## 7.1. DTD练习一

```xml
<!DOCTYPE BOOK [  <!ELEMENT BOOK (TITLE, AUTHOR+, INTRODUCTION?,CHAPTER+)>
<!ELEMENT AUTHOR (LASTNAME?, FIRSTNAME?)>
<!ATTLIST BOOK ISBN CDATA #REQUIRED>
<!ATTLIST AUTHOR ID CDATA #IMPLIED>
<!ELEMENT TITLE (#PCDATA)>
<!ELEMENT INTRODUCTION (TITLE, TEXT?)>
<!ELEMENT CHAPTER (NUM, TITLE, TEXT+)>
<!ELEMENT NUM (#PCDATA)>
<!ELEMENT TEXT (#PCDATA)>
<!ELEMENT LASTNAME (#PCDATA)>
<!ELEMENT FIRSTNAME (#PCDATA)>]>

<BOOK ISBN="DB123">
    <TITLE> Database Systems - The Complete Book. </TITLE>
    <AUTHOR ID="3">
        <LASTNAME>Widom</LASTNAME>
    </AUTHOR>
    <INTRODUCTION>
        <TITLE>Introduction to Databases</TITLE>
        <TEXT>We introduct to Database</TEXT>
    </INTRODUCTION>
    <CHAPTER>
        <NUM>1</NUM>
        <TITLE>The Worlds of Database Systems </TITLE>
        <TEXT>We overview the evolution of database systems.</TEXT>
    </CHAPTER>
    <CHAPTER>
        <NUM>1</NUM>
        <TITLE>The Entity-Relationship Data Model</TITLE>
        <TEXT>We explain the elements of the ER model.</TEXT>
    </CHAPTER>
</BOOK>

<?xml version="1.0" encoding="UTF-8"?>
<!ELEMENT HOSPITALS (HOSPITAL+)>
<!ELEMENT HOSPITAL (NAME,LOCATION,PATIENTS*,DOCTORS*)>
<!ATTLIST HOSPITAL ID ID #REQUIRED>
<!ATTLIST HOSPITAL KIND CDATA "PERSONAL">
<!ELEMENT NAME (#PCDATA)>
<!ELEMENT LOCATION (#PCDATA)>
<!ELEMENT PATIENTS (PATIENT)*>
<!ELEMENT PATIENT (ILLNESS,DOCTOR_ID,JOINING_DATES,AGE?)>
<!ATTLIST PATIENT ID ID #REQUIRED>
<!ATTLIST PATIENT BIRTHDAY CDATA #IMPLIED>
<!ELEMENT ILLNESS (#PCDATA)>
<!ELEMENT DOCTOR_ID (#PCDATA)>
<!ELEMENT JOINING_DATES (#PCDATA)>
<!ELEMENT AGE (#PCDATA)>
<!ELEMENT DOCTORS (DOCTOR)*>
<!ELEMENT DOCTOR (MAJOR,NAME)>
<!ATTLIST DOCTOR ID ID #REQUIRED>

<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE HOSPITALS SYSTEM "hospitals.dtd">
<HOSPITALS>
    <HOSPITAL ID="NO.1" KIND="NATIONAL">
        <NAME>National University Hospital </NAME>
        <LOCATION>
            Singapo </LOCATION>
        <PATIENTS>
            <PATIENT ID="P.11" BIRTHDAY="1971.1.2">
                <ILLNESS>
                    Hepatitis</ILLNESS>
                <DOCTOR_ID> D.14 </DOCTOR_ID>
                <JOINING_DATES>&registe;2013.10.1 </JOINING_DATES>
                <AGE>42 </AGE>
            </PATIENT>
            <PATIENT ID="P.12 " BIRTHDAY="1990.5.12">
                <ILLNESS>Coughing</ILLNESS>
                <DOCTOR_ID> D.13 </DOCTOR_ID>
                <JOINING_DATES>&registe;2013.11.14 </JOINING_DATES>
                <AGE>23 </AGE>
            </PATIENT>
            <PATIENT ID="P.13" BIRTHDAY="1982.11.11">
                <ILLNESS>Heart disease</ILLNESS>
                <DOCTOR_ID>D.14</DOCTOR_ID>
                <JOINING_DATES>&registe;2013.7.8 </JOINING_DATES>
                <AGE>31 </AGE>
            </PATIENT>
        </PATIENTS>
        <DOCTORS>
            <DOCTOR ID="D.13">
                <MAJOR>
                    Gastroenterology </MAJOR>
                <NAME>
                    Zhang san </NAME>
            </DOCTOR>
            <DOCTOR ID="D.14">
                <MAJOR>
                    Cardiology </MAJOR>
                <NAME>
                    Li si </NAME>
            </DOCTOR>
            <DOCTOR ID="D.15">
                <MAJOR> Medicine </MAJOR>
                <NAME>
                    Wang wu </NAME>
            </DOCTOR>
        </DOCTORS>
    </HOSPITAL>
    <HOSPITAL ID="NO.2" KIND="PERSONAL">
        <NAME>
            Nanchang Tumour Hospital </NAME>
        <LOCATION>
            Nanchang </LOCATION>
        <PATIENTS>
            <PATIENT ID="P.14" BIRTHDAY="1991.7.2">
                <ILLNESS>
                    Aastritis </ILLNESS>
                <DOCTOR_ID> D.16 </DOCTOR_ID>
                <JOINING_DATES>&registe;2013.11.1 </JOINING_DATES>
                <AGE>22 </AGE>
            </PATIENT>
            <PATIENT ID="P.15 " BIRTHDAY="1990.5.12">
                <ILLNESS>Anemia </ILLNESS>
                <DOCTOR_ID> D.13 </DOCTOR_ID>
                <JOINING_DATES>&registe;2013.11.15 </JOINING_DATES>
                <AGE>23 </AGE>
            </PATIENT>
            <PATIENT ID="P.16" BIRTHDAY="1989.5.2">
                <ILLNESS>Appendicitis </ILLNESS>
                <DOCTOR_ID>D.16</DOCTOR_ID>
                <JOINING_DATES>&registe;2013.11.8 </JOINING_DATES>
                <AGE>24 </AGE>
            </PATIENT>
        </PATIENTS>
        <DOCTORS>
            <DOCTOR ID="D.16">
                <MAJOR> Internal medicine </MAJOR>
                <NAME>
                    Wang jun</NAME>
            </DOCTOR>
            <DOCTOR ID="D.17">
                <MAJOR>
                    Hematology </MAJOR>
                <NAME>
                    Li si </NAME>
            </DOCTOR>
        </DOCTORS>
    </HOSPITAL>
    <HOSPITAL ID="NO.3" KIND="NATIONAL">
        <NAME>BJ Children’s Hospital </NAME>
        <LOCATION>
            Nanchang </LOCATION>
        <PATIENTS>
            <PATIENT ID="P.17" BIRTHDAY="2010.8.1">
                <ILLNESS>Fever </ILLNESS>
                <DOCTOR_ID> D.18 </DOCTOR_ID>
                <JOINING_DATES>&registe;2013.11.1 </JOINING_DATES>
                <AGE>3</AGE>
            </PATIENT>
        </PATIENTS>
        <DOCTORS>
            <DOCTOR ID="D.18">
                <MAJOR> Internal medicine</MAJOR>
                <NAME>
                    Zhou hua </NAME>
            </DOCTOR>
        </DOCTORS>
    </HOSPITAL>
</HOSPITALS>
```

## 7.2. Schema练习二

```html
<?xml version="1.0" encoding="UTF-8"?>
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema">
    <xsd:element name="HOSPITALS">
        <xsd:complexType>
            <xsd:sequence>
                <xsd:element name="HOSPITAL" type="HosType" minOccurs="1" maxOccurs="unbounded" /> </xsd:sequence>
        </xsd:complexType>
    </xsd:element>
    <xsd:complexType name="HosType">
        <xsd:sequence>
            <xsd:element name="NAME" type="xsd:string" />
            <xsd:element name="LOCATION" type="xsd:string" />
            <xsd:element name="PATIENTS" type="PasType" />
            <xsd:element name="DOCTORS" type="DocsType" /> </xsd:sequence>
        <xsd:attributeGroup ref="ID" />
        <xsd:attribute name="KIND" use="required">
            <xsd:simpleType>
                <xsd:restriction base="xsd:string">
                    <xsd:enumeration value="INTERNATIONAL" />
                    <xsd:enumeration value="NATIONAL" />
                    <xsd:enumeration value="PERSONAL" /> </xsd:restriction>
            </xsd:simpleType>
        </xsd:attribute>
    </xsd:complexType>
    <xsd:complexType name="PasType">
        <xsd:sequence>
            <xsd:element name="PATIENT" type="patient" minOccurs="1" maxOccurs="unbounded" /> </xsd:sequence>
    </xsd:complexType>
    <xsd:complexType name="DocsType">
        <xsd:sequence>
            <xsd:element name="DOCTOR" type="doctor" minOccurs="1" maxOccurs="unbounded" /> </xsd:sequence>
    </xsd:complexType>
    <xsd:complexType name="patient">
        <xsd:sequence>
            <xsd:element name="ILLNESS" type="xsd:string" />
            <xsd:element name="DOCTOR_ID" type="xsd:string" />
            <xsd:element name="JOINING_DATES" type="xsd:date" />
            <xsd:element name="AGE" type="xsd:int" /> </xsd:sequence>
        <xsd:attributeGroup ref="ID" />
        <xsd:attribute name="BIRTHDAY" use="required" type="xsd:date" /> </xsd:complexType>
    <xsd:complexType name="doctor">
        <xsd:sequence>
            <xsd:element name="MAJOR" type="xsd:string" />
            <xsd:element name="NAME" type="xsd:string" /> </xsd:sequence>
        <xsd:attributeGroup ref="ID" /> </xsd:complexType>
    <xsd:attributeGroup name="ID">
        <xsd:attribute name="ID" type="xsd:ID" /> </xsd:attributeGroup>
</xsd:schema>
```

