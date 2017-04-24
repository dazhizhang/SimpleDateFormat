# SimpleDateFormat
java-使用SimpleDateFormat格式化日期

http://zy-email1991.iteye.com/blog/2243021

参考：http://www.cnblogs.com/peida/archive/2013/05/31/3070790.html

java中使用SimpleDateFormat类的构造函数SimpleDateFormat(String str)构造格式化日期的格式,通过format(Date date)方法将指定的日期对象格式化为指定格式的字符串.
 
下面我们来研究一下SimpleDateFormat构造函数中字符串的格式,以及各部分代表的含义:
例如,我们可以用一下格式来格式化日期:
 
Java代码  收藏代码
import java.text.SimpleDateFormat;  
import java.util.Date;  
  
public class TestDateFormat {  
  
    public static void main(String args[]) {  
        Date newTime = new Date();  
        SimpleDateFormat dateFormatter = new SimpleDateFormat("yyyy-MM-dd hh:mm:ss");  
        String formatDate = dateFormatter.format(newTime);  
  
        System.out.println(formatDate);  // 2015-09-13 03:01:26  
    }  
}  
 字符串"yyyy-MM-dd hh:mm:ss",其中:
 
yyyy : 代表年(不去区分大小写) 假设年份为 2015
    "y" , "yyy" , "yyyy" 匹配的都是4位完整的年 如 : "2015"
    "yy" 匹配的是年分的后两位 如 : "15"
    超过4位,会在年份前面加"0"补位 如 "YYYYY"对应"02015"
 
MM : 代表月(只能使用大写) 假设月份为 9
    "M" 对应 "9"
    "MM" 对应 "09"
    "MMM" 对应 "Sep"
    "MMMM" 对应 "September"
    超出4位,仍然对应 "September"
    
dd : 代表日(只能使用小写) 假设为13号
    "d" , "dd" 都对应 "13"
    超出2位,会在数字前面加"0"补位. 例如 "dddd" 对应 "0013"
 
hh : 代表时(区分大小写,大写为24进制计时,小写为12进制计时) 假设为15时
    "H" , "HH" 都对应 "15" , 超出2位,会在数字前面加"0"补位. 例如 "HHHH" 对应 "0015"
    "h" 对应 "3"
    "hh" 对应 "03" , 超出2位,会在数字前面加"0"补位. 例如 "hhhh" 对应 "0003"
 
mm : 代表分(只能使用小写) 假设为32分
    "m" , "mm" 都对应 "32" ,  超出2位,会在数字前面加"0"补位. 例如 "mmmm" 对应 "0032"
 
ss : 代表秒(只能使用小写) 假设为15秒
    "s" , "ss" 都对应 "15" , 超出2位,会在数字前面加"0"补位. 例如 "ssss" 对应 "0015"
 
E : 代表星期(只能使用大写) 假设为 Sunday
    "E" , "EE" , "EEE" 都对应 "Sun"
    "EEEE" 对应 "Sunday" , 超出4位 , 仍然对应 "Sunday"
 
a : 代表上午还是下午,如果是上午就对应 "AM" , 如果是下午就对应 "PM"
 
其中的分隔符"-"可以替换成其他非字母的任意字符(也可以是汉字),例如:
Java代码  收藏代码
import java.text.SimpleDateFormat;  
import java.util.Date;  
  
public class TestDateFormat {  
  
    public static void main(String args[]) {  
        Date newTime = new Date();  
        SimpleDateFormat dateFormatter = new SimpleDateFormat("yyyy年=MM_月dd 日 hh5时+mm分]ss秒");  
        String formatDate = dateFormatter.format(newTime);  
  
        System.out.println(formatDate);  // 2015年=09_月13 日 035时+07分]42秒  
    }  
}  
