#### OJ

```c
#include <stdio.h>
#include <math.h>
#include <stdlib.h>
#include <string.h>

//字符金字塔
void my_print(int n, char a)
{
    for(int i = n - 1; i >= 0; i--)
    {
        for(int j = 0; j < i; j++)  printf(" ");
        for(int j = 0; j < (n - i); j++)    printf("%c ", a);
        printf("\n");
    }
    return;
}
int main()
{
    int n;
    char a;
    scanf("%d %c", &n, &a);
    my_print(n, a);
    return 0;
}

//空心数字金字塔

void my_print(int n)
{
    for (int i = 1; i <= n; i++)
    {
        for (int j = 0; j < n - i; j++)  printf(" ");
        printf("%d", i);
        if(i == 1)  printf("\n");
        if (i > 1 && i < n)
        {
            for (int j = 0; j < 2 * (i - 1) - 1; j++)   printf(" ");
        }
        if(i > 1 && i < n)   printf("%d\n", i);
        if(i == n)
        {
            for(int j = 1; j < 2 * n - 1; j++)  printf("%d", n);
            printf("\n");
        }
    }
}
int main()
{
    int n;
    scanf("%d", &n);
    my_print(n);
    return 0;
}

//使用函数求素数和
int buf[1000];
int cnt = 0, sum = 0;
int Isprime(int a)
{
    if(a == 1)  return 0;
    for(int i = 2; i < a; i++)
        if(a % i == 0)  return 0;
    return 1;
}
void my_print(int m, int n)
{
    for(int i = m; i <= n; i++)
    {
        if(Isprime(i))
        {
            buf[cnt++] = i;
            sum += i;
        }
    }
    for(int i = 0; i < cnt; i++)
    {
        if(i == 0)  printf("Sum of ( ");
        printf(" %d" + !i, buf[i]);
        if(i == cnt - 1)    printf(" ) = %d", sum);
    }
    return;
}
int main()
{
    int m, n;
    scanf("%d %d", &m, &n);
    my_print(m, n);
    return 0;
}

//使用函数求数字个数
int main()
{
    char buf[1000], num;
    int cnt = 0;
    scanf("%s %c", buf, &num);
    int len = strlen(buf);
    for (int i = 0; i < len; i++)    
    {
        if (buf[i] == num) cnt++;
    }
    printf("Number of digit %c in ", num);
    for(int i = 0; i < len; i++)    printf("%c", buf[i]);
    printf(": %d", cnt);
    return 0;
}

//使用函数输出指定范围内完数
int buf[20000];
int cnt = 0, sum = 0, flag = 0;
int Judge(int a)
{
    for(int i = 1; i < a; i++)
    {
        if(a % i == 0)  
        {
            buf[cnt++] = i;
            sum += i;
        }
        if(i == a - 1 && sum == a)  return 1;
    }
    return 0;
}
void print(int m, int n)
{
    for(int i = m; i <= n; i++)
    {
        sum = 0;
        cnt = 0;
        memset(buf, 0, 20000);
        if(Judge(i))
        {
            flag = 1;
            printf("%d =", i);
            for(int j = 0; j < cnt; j++)
            {
                if(j != cnt - 1)    printf(" %d +", buf[j]);
                else printf(" %d\n", buf[j]);   
            }
        }
    }
    if(!flag)   printf("No perfect number");
    return;
}
int main()
{
    int m, n;
    scanf("%d %d", &m, &n);
    print(m, n);
    return 0;
}

//使用函数输出指定范围内的Fibonacci数
void Fib(int lib[])
{
    int i = 2;
    while(i < 10001)
    {
        lib[i] = lib[i - 1] + lib[i - 2];
        i++;
    }
    return;
}
int Judge(int a, int lib[])
{
    for(int i = 0; i < 10001; i++)
    {
        if(lib[i] == a) return 1;
    }
    return 0;
}
int main()
{
    int m, n, cnt = 0;
    int buf[8000];
    int lib[10000] = {1, 1};
    Fib(lib);
    scanf("%d %d", &m, &n);
    for(int i = m; i <= n; i++)
    {
        if(Judge(i, lib))    buf[cnt++] = i;
    }
    for(int i = 0; i < cnt; i++)
    {
        printf(" %d" + !i, buf[i]);
    }
    if(cnt == 0)    printf("No Fibonacci number");
    return 0;
}

//勤奋的大佬
int main()
{
    int t;
    scanf("%d", &t);
    while(t--)
    {
        int x, y, n, sum = 0;
        scanf("%d %d %d", &x, &y, &n);
        for(int i = 1; i <= n; i++)
        {
            if(!(i % (x + 1) || i % (y + 1)))  sum += 36;
        }
        printf("%d\n", sum);
    }
    return 0;
}

//字符合并
char ch[1000000];
int main()
{
    int n, cnt = 0, flag = 0;
    scanf("%d", &n);
    getchar();
    gets(ch);
    for(int i = 0; ch[i] != '#'; i++)
    {
        if(cnt >= n) break;
        if(ch[i] >= 'A' && ch[i] <= 'Z')  
        {
            printf(" %c" + !flag, ch[i]);
            cnt += 1 + flag;
            flag = 1;
        }
        else if(ch[i] != ' ')    
        {
            printf("%c", ch[i]);
            cnt++;
        }
    }
    return 0;
}

//简化的插入排序
int main()
{
    int n, num, flag = 0, ret;
    scanf("%d", &n);
    int arr[100];
    for (int i = 0; i < n; i++) scanf("%d", &arr[i]);
    scanf("%d", &num);
    for (int i = 0; i < n; i++)
    {
        if (!flag && arr[i] > num)  printf("%d " + flag++, num);
        printf("%d ", arr[i]);
        if (i == n - 1 && !flag)    printf("%d ", num); 
    }
    return 0;
}

//交换最小值和最大值
int main()
{
    int n, ret;
    scanf("%d", &n);
    int arr[100];
    for (int i = 0; i < n; i++) scanf("%d", &arr[i]);
    int min = 0, max = 0;
    for (int i = 0; i < n; i++) min = arr[i]<arr[min]?i:min;
    ret = arr[0];
    arr[0] = arr[min];
    arr[min] = ret;
    for (int i = 0; i < n; i++) max = arr[i]>arr[max]?i:max;   
    ret = arr[n - 1];
    arr[n - 1] = arr[max];
    arr[max] = ret;
    for (int i = 0; i < n; i++) printf("%d ", arr[i]);
    return 0;
}

//求一批整数中出现最多的各位数字
int main()
{
    int n, ret, max = 0;
    char num[10] = {'0', '1', '2', '3', '4', '5', '6', '7', '8', '9'};
    int buf[10] = {0};
    char ch[20];
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {   
        scanf("%s", ch);
        for (int k = 0; ch[k] != '\0'; k++)
            for (int j = 0; j < 10; j++)
                if (num[j] == ch[k])   buf[j]++;
    }
    for (int i = 0; i < 10; i++)    max = buf[i]>buf[max]?i:max;
    printf("%d:", buf[max]);
    for (int i = 0; i < 10; i++)    if (buf[i] == buf[max]) printf(" %c", num[i]);
    return 0;   
}

//找出不是两个数组共有的元素
#include <stdio.h>
#include <string.h>
int main()
{
    int a, b, aarr[2][100], barr[2][100], flag = 0;
    memset(aarr, 0, sizeof(aarr));
    memset(barr, 0, sizeof(barr));
    scanf("%d", &a);
    for (int i = 0; i < a; i++) scanf("%d", &aarr[0][i]);
    scanf("%d", &b);
    for (int i = 0; i < b; i++) scanf("%d", &barr[0][i]);
    for (int i = 0; i < a; i++)
    {
        for (int j = 0; j < b; j++)
                if (aarr[0][i] == barr[0][j])
                {
                    aarr[1][i] = 1;
                    barr[1][j] = 1;
                }
    }
    for (int i = 0; i < a; i++) 
    {
        for (int j = i + 1; j < a; j++)
            if (aarr[0][i] == aarr[0][j])  aarr[1][j] = 1;
    }
    for (int i = 0; i < b; i++) 
    {
        for (int j = i + 1; j < b; j++)
            if (barr[0][i] == barr[0][j])  barr[1][j] = 1;
    }
    for (int i = 0; i < a; i++) 
    {
        if (!aarr[1][i])  
        {
            printf(" %d" + !flag, aarr[0][i]);
            flag = 1;
        }
    }
    for (int i = 0; i < b; i++)
    {
        if (!barr[1][i])  
        {
            printf(" %d" + !flag, barr[0][i]);
            flag = 1;
        }
    }
    return 0;
}

//求整数序列中出现次数最多的数
int main()
{
    int n, a, cnt = 0, max = 0, arr[2][1500];
    memset(arr, 0, sizeof(arr));
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {
        int flag = 1;
        scanf("%d", &a);
        for (int j = 0; j < cnt; j++)
        {
            if (arr[0][j] == a) 
            {
                arr[1][j]++;
                flag = 0;
                break;
            }
        }
        if (flag == 1)  
        {
            arr[1][cnt] = 1;
            arr[0][cnt++] = a;
        }
    }
    for (int i = 0; i < cnt; i++)
        max = arr[1][i]>arr[1][max]?i:max;
    printf("%d %d", arr[0][max], arr[1][max]);
    return 0;
}

//奖金提成
double Awd(int mon)
{
    double sum;
    switch(mon/10000)
    {
        case 0: sum = mon * 0.1;
                break;
        case 1: sum = 10000 * 0.1 + (mon - 10000) *0.075;
                break;
        case 2:
        case 3: sum = 10000 * 0.1 + 10000 * 0.075 + (mon - 20000) * 0.05;
                break;
        case 4: 
        case 5: sum = 10000 * 0.1 + 10000 * 0.075 + 20000 * 0.05 + (mon - 40000) * 0.03;
                break;
        case 6:
        case 7:
        case 8:
        case 9: sum = 10000 * 0.1 + 10000 * 0.075 + 20000 * 0.05 + 20000 * 0.03 + (mon - 60000) * 0.015;
                break;
        default:
                sum = 10000 * 0.1 + 10000 * 0.075 + 20000 * 0.05 + 20000 * 0.03 + 40000 * 0.015 + (mon - 100000) * 0.01;
                break;
    }
    return sum;
}
int main()
{
    int t, mon;
    scanf("%d", &t);
    while (t--)
    {
        scanf("%d", &mon);
        printf("%0.lf\n", Awd(mon));
    }
    return 0;
}

//扫雪挑战
int buf[1000100] = {0};
int main()
{
    int len, t, cnt = 0;
    scanf("%d %d", &len, &t);
    while (t--)
    {
        int m, n;
        scanf("%d %d", &m, &n);
        for (int i = m; i <= n; i++) buf[i] = 1;
    }
    for (int i = 1; i <= len; i++)   if (!buf[i]) cnt++;
    printf("%d", cnt);
    return 0;
}
```

#### ACM

[百练题单][百练题单-热门题-从易到难 - Virtual Judge (csgrandeur.cn)](https://vjudge.csgrandeur.cn/article/3191)

```c++
//大整数除法
int main()
{
    char a[210] = {0}, b[210] = {0};
    cin >> a >> b;
    int aa[210], bb[210], tmp, flag = 0;
    memset(aa, 0, 210);
    memset(bb, 0, 210);
    int al = strlen(a), bl = strlen(b);
    for (int i = al; i > 0; i--)   aa[al - i + 1] = a[i - 1] - '0';
    for (int i = bl; i > 0; i--)   bb[bl - i + 1] = b[i - 1] - '0';
    int buf[100000] = {0};
    for (int i = 1; i <= bl; i++)
    {
        for (int j = 1; j <= al; j++)
        {
            tmp = bb[i] * aa[j] + buf[i + j - 1];
            buf[i + j - 1] = tmp % 10;
            buf[i + j]  += tmp / 10;
        }
    }
    for (int i = al + bl; i > 0; i--)
    {
        if (buf[i] != 0)  flag = 1;
        if (flag || i == 1)   cout << buf[i];
    }
    return 0;
}
```



[STL](https://vjudge.csgrandeur.cn/contest/529954#overview)

```c++
//单词数
#include <iostream>
#include <string>
#include <set>
using namespace std;
int main()
{
    string str;
    while (getline(cin, str))
    {
        set<string> se;
        if (str[0] == '#')  break;
        string t = "";
        for (int i = 0; i < str.size(); i++)
        {
            if (str[i] == ' ' || i == str.size() - 1)
            {
                if (t.size() == 0)  continue;
                else se.insert(t);
                t = "";
            }
            else
                t += str[i];
        }
        printf("%d\n", se.size());
    }
    return 0;
}

//操作栈
#include <iostream>
#include <stack>
using namespace std;
int main()
{
    stack<int> stk;
    int n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {
        int op;
        scanf("%d", &op);
        if (op == 1)
        {
            int x;
            scanf("%d", &x);
            stk.push(x);
        }
        else
        {
            if (stk.empty())    printf("empty\n");
            else
            {
                printf("%d\n", stk.top());
                stk.pop();
            }
        }
    }
    return 0;
}

//操作队列
#include <iostream>
#include <string>
#include <queue>
using namespace std;
int main()
{
    queue<int> que;
    int n;
    scanf("%d", &n);
    for (int i = 0; i < n; i++)
    {
        int op;
        scanf("%d", &op);
        if (op == 1)
        {
            int a;
            scanf("%d", &a);
            que.push(a);
        }
        else
        {
            if(que.empty()) printf("empty\n");
            else
            {
                printf("%d\n", que.front());
                que.pop();
            }
        }
    }
    return 0;
}

//愚人节的礼物
#include <iostream>
#include <string>
#include <cstring>
#include <stack>
using namespace std;
char s[1005];
int main()
{
    stack<char> stk;
    while (scanf("%s", s) != EOF)
    {
        int len = strlen(s);
        for (int i = 0; i < len; i++)
        {
            if (s[i] == '(')    stk.push('(');
            else if (s[i] == ')')    stk.pop();
            else if (s[i] == 'B')   printf("%d\n", stk.size());
        }
    }
    return 0;
}

//Train Problem I
#include <iostream>
#include <string>
#include <cstring>
#include <queue>
#include <stack>
using namespace std;
const int N = 15;
char a[N], b[N];
int main()
{
    int n;
    while (scanf("%d%s%s", &n, a + 1, b + 1) != EOF)
    {
        vector<int> ve;
        int j = 1;
        stack<char> stk;
        int fl = 1;
        for (int i = 1; i <= n; i++)
        {
            stk.push(a[i]);
            ve.push_back(1);
            while (!stk.empty() && stk.top() == b[j])
            {
                stk.pop();
                j++;
                ve.push_back(0);
            }
        }
        if (j <= n) fl = 0;
        if (stk.empty() && fl)
        {
            printf("Yes.\n");
            for (int i = 0; i < ve.size(); i++)
            {
                if (ve[i] == 0) printf("out\n");
                else printf("in\n");
            }
        }
        else 
            printf("No.\n");
        printf("FINISH\n");
    }
    return 0;
}

//Let the Balloon Rise
#include <iostream>
#include <string>
#include <cstring>
#include <stack>
#include <map>
using namespace std;
int main()
{
    int n;
    while(cin >> n)
    {
        if(!n)	break;
        map<string, int> ma;
        for(int i = 0; i < n; i++)
        {
            string s;
            cin >> s;
            ma[s]++;
        }
        string ret;
        int cmp = 0;
        for(auto it = ma.begin(); it != ma.end(); it++)
        {
            if(it -> second > cmp)
            {
                cmp = it -> second;
                ret = it -> first;
            }
        }
        cout << ret << endl;
    }
    return 0;
}

//水果
#include <iostream>
#include <string>
#include <cstring>
#include <stack>
#include <map>
using namespace std;
int main()
{
    int t;
    cin >> t;
    while(t--)
    {
        int n;
        cin >> n;
        map<string, map<string, int>> ma;
        for(int i = 0; i < n; i++)
        {
            string fruits, area;
            int num;
            cin >> fruits >> area >> num;
            ma[area][fruits] += num;
        }
        for(auto it = ma.begin(); it != ma.end(); it++)
        {
            cout << it -> first << endl;
            for(auto itt = it -> second.begin(); itt != it -> second.end(); itt++)
            {
                cout << "   |----" << itt -> first << "(" << itt -> second << ")" << endl;
            }
        }
        if(t)   cout << endl;
    }
    return 0;
}

//stones
#include <iostream>
#include <string>
#include <cstring>
#include <queue>
using namespace std;
struct node
{
    int pos, dis;
    bool operator<(const node &t) const
    {
        if (pos != t.pos)
            return pos > t.pos;
        return dis > t.dis;
    }
};
int main()
{
    int t;
    cin >> t;
    while(t--)  
    {
        int n;
        cin >> n;
        priority_queue<node> que;
        for (int i = 0; i < n; i++)
        {
            node b;
            scanf("%d%d", &b.pos, &b.dis);
            que.push(b);
        }
        int res = 0;
        int flag = 0;
        while (que.size())
        {
            if (!flag)
            {
                node b;
                b.dis = que.top().dis;
                b.pos = que.top().dis + que.top().pos;
                que.pop();
                que.push(b);
                flag ^= 1;
                if(que.size() == 1)
                {
                    res = que.top().pos;
                    break;
                }
            }
            else 
            {
                que.pop();
                flag ^= 1;
            }
        }
        printf("%d\n", res);
    }
    return 0;
}

//Windows Message Queue
#include <iostream>
#include <string>
#include <cstring>
#include <queue>
using namespace std;
struct node
{
    int num;
    int val;
    int val2;
    string name;
    bool operator<(const node &t) const
    {
        if (val != t.val)
            return val > t.val;
        else 
            return val2 > t.val2;
    }
};
int main()
{
    string s;
    priority_queue<node> que;
    int id = 1;
    while (cin >> s)
    {
        if (s == "GET")
        {
            if (que.empty())
                cout << "EMPTY QUEUE!\n";
            else 
            {
                cout << que.top().name << " " << que.top().num << endl;
                que.pop();
            }
        }
        else 
        {
            string name;
            int num, val;
            cin >> name >> num >> val;
            que.push({num, val, id, name});
        }
        id++;
    }
    return 0;
}
```

#### Game1

```c++
//头文件的包含
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

//函数的定义
#define ROW 3
#define COL 3


//函数的声明


//初始化棋盘
void Initboard(char board[ROW][COL],int row,int col);

//打印棋盘的函数
void Displayboard(char board[ROW][COL], int row, int col);

//玩家下棋
void PlayerMove(char board[ROW][COL], int row, int col);

//电脑下棋
void ComputerMove(char board[ROW][COL], int row, int col);

//判断输赢
char Iswin(char board[ROW][COL], int row, int col);

 void Initboard(char board[ROW][COL], int row, int col)
{
	 int i = 0;
	 int j = 0;
	 for (i = 0; i < row; i++)
	 {
		 for (j = 0; j < col; j++)
		 {
			 board[i][j] = ' ';
		 }
	 }
}


 void Displayboard(char board[ROW][COL], int row, int col)
 {
	 int i = 0;
	 for (i = 0; i < row; i++)
	 {
		 int j = 0;
		 for (j = 0; j < col;j++)
		 {
			 printf(" %c ",board[i][j]);
			 if (j < col - 1)
				 printf("|");
		 }
		 printf("\n");
		 if (i < row - 1)
		 {
			 int j = 0;
			 for (j = 0; j < col; j++)
			 {
				 printf("---");
				 if (j < col - 1)
					 printf("|");
			 }
		 }
		 printf("\n");
	 }
 }



 void PlayerMove(char board[ROW][COL], int row, int col)
 {
	 int x = 0;
	 int y = 0;
	 printf("Player Move\n");
	 printf("Please enter coordinates\n");
	 while (1)
	 {
		 scanf("%d %d", &x, &y);
		 //判断坐标合法性
		 if (x >= 1 && x <= row && y >= 1 && y <= col)
		 {
			 //下棋
			 //判断是否被占用
			 if (board[x - 1][y - 1]==' ')
			 {
				 board[x - 1][y - 1] = '*';
				 break;
			 }
			 else
			 {
				 printf("Coordinates have been occupied,please re-enter.\n");
			 }
		 }
		 else
		 {
			 printf("The coordinates are illegal,please re-enter.\n");
		 }
	 }
 }

 void ComputerMove(char board[ROW][COL], int row, int col)
 {
	 printf("Turn to computer\n");
	 while (1)
	 {
		 int x = rand() % row;
		 int y = rand() % col;
		 //判断占用
		 if (board[x][y] == ' ')
		 {
			 board[x][y] = '#';
			 break;
		 }
	 }
 }




 Isfull(char board[ROW][COL], int row, int col)
 {
	 int i = 0;
	 int j = 0;
	 for (i = 0; i < row; i++)
	 {
		 for (j = 0; j < col; j++)
		 {
			 if (board[i][j] == ' ')
				 return 0;//棋盘没满
		 }
	 }
	 return 1;//棋盘已满
 }

 char Iswin(char board[ROW][COL], int row, int col)
 {
	 int i = 0;
	 //判断行
	 for (i = 0; i < row; i++)
	 {
		 if (board[i][0] == board[i][1] && board[i][1] == board[i][2] && board[i][1] != ' ')
		 {
			 return board[i][1];
		 }
	 }
	 //判断列
	 for (i = 0; i< col; i++)
	 {
		 if (board[0][i] == board[1][i] && board[1][i] == board[2][i] && board[0][i] != ' ')
		 {
			 return board[1][i];
		 }
	 }
	 //判断对角线
	 if (board[0][0] == board[1][1] && board[1][1] == board[2][2] && board[0][0] != ' ')
	 {
		 return board[0][0];
	 }
	 if (board[0][2] == board[1][1] && board[1][1] == board[2][0] && board[0][2] != ' ')
	 {
		 return board[0][2];
	 }
	 //判断是否平局
	 int ret=Isfull(board, row, col);
	 if (ret == 1)
	 {
		 return 'Q';
	 }
	 return 'c';
 }

void menu()
{
	printf("1.play\n");
	printf("0.exit\n");
}

void game()
{
	//储存数据-二维数组
	char board[ROW][COL];
	//初始化棋盘-初始化空格
	Initboard(board, ROW, COL);
	//打印棋盘-本质是打印数组内容
	Displayboard(board, ROW, COL);
	char ret = 0;
	while (1)
	{
		//玩家下棋
		PlayerMove(board, ROW, COL);
		Displayboard(board, ROW, COL);
		//判断玩家是否赢得游戏
		ret = Iswin(board, ROW, COL);
		if (ret != 'c')
			break;
		//电脑下棋
		ComputerMove(board, ROW, COL);
		Displayboard(board, ROW, COL);
		//判断电脑是否赢得游戏
		ret = Iswin(board, ROW, COL);
		if (ret != 'c')
			break;
	}
	if (ret == '*')
	{
		printf("Player Win!\n");
	}
	else if (ret == '#')
	{
		printf("Computer Win!\n");
	}
	else
	{
		printf("Q.\n");  
	}
	Displayboard(board, ROW, COL);

}


int main()
{
	int input = 0;
	srand((unsigned int)time(NULL));	//设置随机值
	do
	{
		menu();
		scanf("%d", &input);
		switch(input)
		{
		case 1:
			    game();
				break;
		case 0:
				printf("Quit the game\n");
				break;
		default :
				printf("Incorrect selection,please reselect\n");
				break;
		}
	} while (input);

	return 0;
}
```

#### Others

[约瑟夫问题](https://vjudge.csgrandeur.cn/problem/OpenJ_Bailian-2746)

```c++
#include <stdio.h>
#include <math.h>
#define MAX 10010

    int main()
    {
        int mon[300] = {0};
        int n, m, cnt;
        int out;
        while(scanf("%d %d", &n, &m) && n != 0 && m != 0)//111111
        {
            out = 0;
            cnt = 0;
            for(int i = 0; i < n; i ++)   mon[i] = 1;
            for(int i = 0; i < n && n != 1; i ++)
            {
                if(out == n-1 && i == n - 1)    break;
                if(mon[i] != 0) cnt++;
                if(cnt == m)    
                {
                    mon[i] = 0;
                    cnt = 0;
                    out++;
                }
                if(out != n-1 && i == n - 1)
                {
                    i = -1;
                }
            }
            for(int i = 0; i< n; i ++)
                if(mon[i] == 1) printf("%d\n", i+1);
        }
        return 0;
    }
```

圆桌问题

```c++
#include <iostream>
#include <vector>
using namespace std;

int main()
{
    vector<int> table;
    int n, m;
    while (cin >> n >> m)
    {
        table.clear();
        int pos = 0;
        for (int i = 0; i < n; i++)
        {
            pos = (pos + m - 1) % table.size();
            table.erase(table.begin() + pos);
        }
        int j = 0;
        for (int i = 0; i < 2 * n; i++)
        {
            if (!(i % 50) && i) cout << endl;
            if (j < table.size() && i == table[j])
            {
                j++;
                cout << "G";
            }
            else
                cout << "B";
        }
        cout << endl << endl;
    }
    return 0;
}
```

“Text Reverse"

```c++
#include <iostream>
#include <vector>
#include <stack>
using namespace std;

int main()
{
    int n;
    char ch;
    cin >> n;
    cin.get();
    while (n--)
    {
        stack<char> s;
        while (true)
        {
            ch = cin.get();
            if (ch == ' ' || ch == '\n' || ch == EOF)
            {
                while (!s.empty())
                {
                    cout << s.top();
                    s.pop();
                }
                if (ch == '\n' || ch == EOF)    break;
                cout << ' ';            
            }
            else    s.push(ch);
        }
        cout << endl;
    }
    return 0;
}
```

"ACboy needs your help again!"

```c++
//模拟栈和队列
#include <iostream>
#include <vector>
#include <stack>
#include <queue>
using namespace std;

int main()
{
    int t, n, temp;
    cin >> t;
    while (t--)
    {
        string str, str1;
        queue<int> Q;
        stack<int> S;
        cin >> n >> str;
        for (int i = 0; i < n; i++)
        {
            if (str == "FIFO")          //队列
            {
                cin >> str1;
                if (str1 == "IN")
                {
                    cin >> temp;
                    Q.push(temp);
                }
                if (str1 == "OUT")
                {
                    if (Q.empty())  cout << "None" << endl;
                    else{
                        cout << Q.front() << endl;
                        Q.pop();
                    }
                }
            }
            else                        //栈
            {
                if (str1 == "IN")
                {
                    cin >> temp;
                    S.push(temp);
                }
                if (str1 == "OUT")
                {
                    if (S.empty())  cout << "None" << endl;
                    else
                    {
                        cout << S.top() << endl;
                        S.pop();
                    }
                }
            }
        }
    }
    return 0;
}
```


