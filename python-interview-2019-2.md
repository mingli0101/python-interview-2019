## Python开发工程师笔试题

> 答题要求：将该项目从[地址1](<https://github.com/jackfrued/python-interview-2019>)或[地址2](<https://gitee.com/jackfrued/python-interview-2019>)fork到自己的[github]()或[gitee]()仓库并填写答案，完成之后将自己的仓库（public）地址发给面试官即可，答题时间120分钟。

1. 下面的Python代码会输出什么。

   ```Python
   print([(x, y) for x, y in zip('abcd', (1, 2, 3, 4, 5))])
   print({x: f'item{x ** 2}' for x in range(5) if x % 2})
   print(len({x for x in 'hello world' if x not in 'abcdefg'}))
   ```


   
  

   ```   
   答案：[(a,1),(b,2),(c,3),(d,4)]
   {'1':item1,'1':item9}
    2
   ```

2. 下面的Python代码会输出什么。

   ```Python
   from functools import reduce
   
   items = [11, 12, 13, 14] 
   print(reduce(int.__mul__, map(lambda x: x // 2, filter(lambda x: x ** 2 > 150, items))))
   ```

   答案：
   
   

   ```
   42
   ```

3. 有一个通过网络获取数据的Python函数（可能会因为网络或其他原因出现异常），写一个装饰器让这个函数在出现异常时可以重新执行，但尝试重新执行的次数不得超过指定的最大次数。

   答案：

   ```Python
   def god():
      def set(*args,**kwargs):
         try:
            func()
         except:
            for i in range(4):
               if func():
                  break
       return set
   
   ```

4. 下面的字典中保存了某些公司今日的股票代码及价格，用一句Python代码从中找出价格最高的股票对应的股票代码，用一句Python代码创建股票价格大于100的股票组成的新字典。

   > 说明：美股的股票代码是指英文字母代码，如：AAPL、GOOG。

   ```Python
   prices = {
       'AAPL': 191.88,
       'GOOG': 1186.96,
       'IBM': 149.24,
       'ORCL': 48.44,
       'ACN': 166.89,
       'FB': 208.09,
       'SYMC': 21.29
   }
   ```
   
   
   答案：

   ```Python
   print(sorted(zip(prices.values(),prices.keys()))[-1][1])
   print([{i[1]:i[0]} for i in sorted(zip(prices.values(),prices.keys())) if i[0] >100])
   
   ```

5. 用生成式实现矩阵的转置操作。例如，用`[[1, 2], [3, 4], [5, 6]`表示矩阵$\begin{bmatrix}1 & 2\\\\3 &4\\\\5 & 6\end{bmatrix}$，写一个生成式将其转换成`[[1, 3, 5], [2, 4, 6]]`即$\begin{bmatrix}1 & 3 & 5\\\\2 & 4 & 6\end{bmatrix}$。

   答案：

   ```Python
   f = [list((e[0],e[1])) for e in d]
   ```

6. 写一个函数，传入的参数是一个列表（列表中的元素可能也是一个列表），返回该列表最大的嵌套深度，例如：

   > 参数：`[1, 2, 3]`
   >
   > 返回：`1`
   >
   > 参数：`[[1], [2, [3]]]`
   >
   > 返回：`3`

   答案：

   ```Python
   
   ```

7. 写一个函数，实现将输入的长链接转换成短链接，每个长链接对应的短链接必须是独一无二的且每个长链接只应该对应到一个短链接，假设短链接统一以`http://t.cn/`开头。

   > 参数：`http://jackfrued.xyz/api/users/10001`
   >
   > 返回：`http://t.cn/E6MUth1`

   答案：

   ```Python
   a = random.choice('anbegvdje')
   b = random.choice('ASGKJAHQEJ')
   c = random.choice('1234567890')
   e = b+c+b+b+a+a+c
   e = 'http://t.cn/' + e
   ```

8. 用5个线程，将1~100的整数累加到一个初始值为0的变量上，每次累加时将线程ID和本次累加后的结果打印出来。

    答案：

    ```Python
    results = []
    def f():
      results.append(sum(i,os.gettid() for i in range(1,101)))
    
    def main():
      threads = [threading.Thread(target = f)for _ in range(5)]
      for thread in threads:
         thread.start()
         print(os.gettid())
      for thread in threads:
         thread.join()
      print('results')
      
    
    ```

9. 请阐述Python是如何进行内存管理的。

    答案：

    ```
    一、垃圾回收：从经过引用计数器机制后还没有被释放掉内存的对象中，找到循环引用对象，并释放掉其内存二、引用计数：Python采用了类似Windows内核对象一样的方式来对内存进行管理。每一个对象，都维护这一个对指向该对对象的引用的计数。 三、内存池机制python又分为大内存和小内存。大小以256字节为界限，对于大内存使用Malloc进行分配，而对于小内存则使用内存池进行分配。

    
    ```

10. 在MySQL数据库中有名为`tb_result`的表如下所示，请写出能查询出如下所示结果的SQL。

  `tb_result`表：

  | rq         | shengfu |
  | ---------- | ------- |
  | 2017-04-09 | 胜      |
  | 2017-04-09 | 胜      |
  | 2017-04-09 | 负      |
  | 2017-04-09 | 负      |
  | 2017-04-10 | 胜      |
  | 2017-04-10 | 负      |
  | 2017-04-10 | 负      |

  查询结果：

  | rq         | 胜   | 负   |
  | ---------- | ---- | ---- |
  | 2017-04-09 | 2    | 2    |
  | 2017-04-10 | 1    | 2    |

  答案：

  ```SQL
  select rq,shengfu from tb_result;
  
  
  ```

11. 列举出你知道的HTTP请求头选项并说明其作用。

    答案：

    ```
    user-agent
    proxy
    
    
    ```

12. 阐述JSON Web Token的工作原理和优点。

    答案：

    ```
    原理：服务器认证以后，生成一个 JSON 对象，返回用户。
    用户与服务端通信的时候，都要发回这个 JSON 对象。服务器靠这个对象认定用户身份。为了防止用户篡改数据，服务器在生成这个对象的时候，会加上签名。
    优点：服务器就不保存任何 session 数据了，也就是说，服务器变成无状态了，从而比较容易实现扩展。
    ```

13. 请阐述访问一个用Django或Flask开发的Web应用，从用户在浏览器中输入网址回车到浏览器收到Web页面的整个过程中，到底发生了哪些事情，越详细越好。

    答案：

    ```
    访问网站-web浏览器请求网站资源-web服务器，与数据库进行数据交互-返回网站资源给web浏览器-返回网站页面
    ```

14. 请阐述HTTPS的工作原理，并说明该协议与HTTP之间的区别。

    答案：

    ```
    客户端发起HTTPS请求，服务器将数字证书返回给浏览器 浏览器进入数字证书认证环节，查到了对应的机构，则取出该机构颁发的公钥，用机构的证书公钥解密得到证书的内容和证书签名，内容包括网站的网址、网站的公钥、证书的有效期等，浏览器生成一个随机数R，并使用网站公钥对R进行加密，浏览器将加密的R传送给服务器。服务器用自己的私钥解密得到R。服务器以R为密钥使用了对称加密算法加密网页内容并传输给浏览器。浏览器以R为密钥使用之前约定好的解密算法获取网页内容。
    在HTTP上又加了一层处理加密信息的模块。服务端和客户端的信息传输都会通过TLS进行加密，所以传输的数据都是加密后的数据
    ```

15. 简述如何检查数据库是不是系统的性能瓶颈以及你在工作中是如何优化数据库操作性能的。

    答案：

    ```
  减少数据访问，返回更少数据，减少交互次数，减少服务器CPU开销，利用更多资源
    ```

16. 在Linux系统中，假设Nginx的访问日志位于`/var/log/nginx/access.log`，该文件的每一行代表一条访问记录，每一行都由若干列（以制表键分隔）构成，其中第1列记录了访问者的IP地址。请用一条命令找出最近的100000次访问中，访问频率最高的IP地址及访问次数。

    答案：

    ```Shell
    import pandas as pd
    note = pd.read_table(`/var/log/nginx/access.log`)
    n = note.iloc[:,[0]]
    max_ip = n.value_counts()
    max_ip.iloc[0]
    ```

