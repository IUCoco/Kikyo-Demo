# Kikyo-Demo
以前自己写的Demo  
![](/2016-12-28%2021.57.39.gif)  

下拉刷新、上拉加载更多数据问题，比如每次加载三条数据  
[40、39、38、37、36、35、34、33......5、4、3、2、1、0]  
@1上拉加载更多数据，需要获取当前页的最大maxtime,才能判断追加更多数据的准确性。比如当前页最大maxtime为12，那么下一次上拉加载更多的id为13、14、15。  
@2下拉刷新问题  
1.如果追加可能导致有的数据加载不到。比如当前最大为40，服务器更新了45、44、43、42、41五条数据每次追加最前面三条。45、44、43、40、39、、、0此时数据造成丢失，可以用覆盖来避免这种情况。如果服务器给了当前最大参数，那么久更好了  
2.比如当前最大为40，服务器更新了42、41五条数据每次追加最前面三条。42、41、40、--->40、39、、、0此时数据冗余  

@3下拉刷新、上拉加载更多共存问题  当前页面40、39、38.如果下拉刷新先完成此时数据覆盖后变为43、42、41.然后上拉加载更多。37、36、35、三条追加。此时43、42、41、37、36、35又造成数据丢失  
