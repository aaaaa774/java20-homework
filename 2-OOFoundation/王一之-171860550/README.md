程序分为四个文件中四个类，分别为Unit、HuLuWa、Tile、LineUp

Unit为单位类，是之后所有单位（如葫芦娃、妖怪等）的父类，目前只有一个属性：
int pos 表示位置，-1表示暂无位置

HuLuWa为葫芦娃类，继承Unit类，成员变量如下：
final int rank//排名
final enum color
方法除构造函数外，有compareRank方法，功能是和传入的葫芦娃比较rank大小

Tile类为格子，可容纳一个单位，成员变量如下：
private Unit member;//格子上的单位
boolean isEmpty;//是否为空
final int pos;//位置编号
方法如下：
构造函数分为直接生成与上面占有单位的生成。
public Unit leave()//若不为空，更新member.pos与isEmpty，将member置空，
public boolean enter(Unit m)//若为空，将member置为m，更新m.pos与isEmpty
public Unit getMember()//返回member
public static void swap(Tile ga, Tile gb)//交换两个格子的成员

LineUp为列队，是控制类
方法如下：
public static void sortChoreography(Tile[] g, HuLuWa[] hulu)
//通过hulu访问每一个葫芦娃，每个身后有人的葫芦娃看自己是否需要和身后交换位置，不断重复，若某一次没有葫芦娃需要交换位置，则结束排序
public static void sortOrchestration(Tile[] g)
//直接对g上的成员进行排序，此处用了冒泡排序
public static void randomInit(Tile[] g, HuLuWa[] h)
//将hulu随机分配到g上
public static void printTile(Tile[] g)
//打印g上的所有成员
public static void main(String[] args)

main函数中，首先，在一个HuLuWa数组中生成7个葫芦娃；之后生成ground，为Tile数组，调用randomInit将葫芦娃随机分配到ground中，之后排序并打印，为了区分两个排序方法，第一次降序，第二次升序。