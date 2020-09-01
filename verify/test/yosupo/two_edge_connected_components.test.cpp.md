---
layout: default
---

<!-- mathjax config similar to math.stackexchange -->
<script type="text/javascript" async
  src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/MathJax.js?config=TeX-MML-AM_CHTML">
</script>
<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    TeX: { equationNumbers: { autoNumber: "AMS" }},
    tex2jax: {
      inlineMath: [ ['$','$'] ],
      processEscapes: true
    },
    "HTML-CSS": { matchFontHeight: false },
    displayAlign: "left",
    displayIndent: "2em"
  });
</script>

<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/jquery-balloon-js@1.1.2/jquery.balloon.min.js" integrity="sha256-ZEYs9VrgAeNuPvs15E39OsyOJaIkXEEt10fzxJ20+2I=" crossorigin="anonymous"></script>
<script type="text/javascript" src="../../../assets/js/copy-button.js"></script>
<link rel="stylesheet" href="../../../assets/css/copy-button.css" />


# :heavy_check_mark: test/yosupo/two_edge_connected_components.test.cpp

<a href="../../../index.html">Back to top page</a>

* category: <a href="../../../index.html#0b58406058f6619a0f31a172defc0230">test/yosupo</a>
* <a href="{{ site.github.repository_url }}/blob/master/test/yosupo/two_edge_connected_components.test.cpp">View this file on GitHub</a>
    - Last commit date: 2020-03-12 16:29:30+09:00


* see: <a href="https://judge.yosupo.jp/problem/two_edge_connected_components">https://judge.yosupo.jp/problem/two_edge_connected_components</a>


## Depends on

* :heavy_check_mark: <a href="../../../library/graph/twoedgeconnectedcomponents.cpp.html">graph/twoedgeconnectedcomponents.cpp</a>


## Code

<a id="unbundled"></a>
{% raw %}
```cpp
#define PROBLEM "https://judge.yosupo.jp/problem/two_edge_connected_components"

#include<bits/stdc++.h>
using namespace std;

#define call_from_test
#include "../../graph/twoedgeconnectedcomponents.cpp"
#undef call_from_test

signed main(){
  cin.tie(0);
  ios::sync_with_stdio(0);

  int n,m;
  cin>>n>>m;

  TwoEdgeConnectedComponents C(n);
  for(int i=0;i<m;i++){
    int a,b;
    cin>>a>>b;
    C.add_edge(a,b);
  }

  int k=C.build();
  cout<<k<<endl;
  for(int i=0;i<k;i++){
    cout<<C[i].size();
    for(int j=0;j<(int)C[i].size();j++) cout<<" "<<C[i][j];
    cout<<"\n";
  }

  cout<<flush;
  return 0;
}

```
{% endraw %}

<a id="bundled"></a>
{% raw %}
```cpp
#line 1 "test/yosupo/two_edge_connected_components.test.cpp"
#define PROBLEM "https://judge.yosupo.jp/problem/two_edge_connected_components"

#include<bits/stdc++.h>
using namespace std;

#define call_from_test
#line 2 "graph/twoedgeconnectedcomponents.cpp"

#ifndef call_from_test
#line 5 "graph/twoedgeconnectedcomponents.cpp"
using namespace std;
#endif
//BEGIN CUT HERE
// work with multigraph
struct TwoEdgeConnectedComponents{
  vector<int> ord,low,par,blg,sz;
  vector<vector<int>> G,C;

  TwoEdgeConnectedComponents(int n):
    ord(n,-1),low(n),par(n,-1),blg(n,-1),sz(n,1),G(n){}

  void add_edge(int u,int v){
    if(u==v) return;
    G[u].emplace_back(v);
    G[v].emplace_back(u);
  }

  bool is_bridge(int u,int v){
    if(ord[u]>ord[v]) swap(u,v);
    return ord[u]<low[v];
  }

  void dfs(int v,int &pos){
    ord[v]=low[v]=pos++;
    int dup=0;
    for(int u:G[v]){
      if(u==par[v] and !dup){
        dup=1;
        continue;
      }
      if(~ord[u]){
        low[v]=min(low[v],ord[u]);
        continue;
      }
      par[u]=v;
      dfs(u,pos);
      sz[v]+=sz[u];
      low[v]=min(low[v],low[u]);
    }
  }

  void fill_component(int v){
    C[blg[v]].emplace_back(v);
    for(int u:G[v]){
      if(~blg[u]||is_bridge(u,v)) continue;
      blg[u]=blg[v];
      fill_component(u);
    }
  }

  void add_component(int v,int &k){
    if(~blg[v]) return;
    blg[v]=k++;
    C.emplace_back();
    fill_component(v);
  }

  int build(){
    int n=G.size(),pos=0;
    for(int i=0;i<n;i++)
      if(ord[i]<0) dfs(i,pos);

    int k=0;
    for(int i=0;i<n;i++) add_component(i,k);

    return k;
  }

  const vector<int>& operator[](int i)const{return C[i];}

  vector<vector<int>> forest(){
    int n=G.size(),k=C.size();
    vector<vector<int>> T(k);
    for(int v=0;v<n;v++)
      for(int u:G[v])
        if(blg[v]!=blg[u])
          T[blg[v]].emplace_back(blg[u]);
    return T;
  }
};
//END CUT HERE
#ifndef call_from_test
//INSERT ABOVE HERE
signed main(){
  return 0;
}
#endif
#line 8 "test/yosupo/two_edge_connected_components.test.cpp"
#undef call_from_test

signed main(){
  cin.tie(0);
  ios::sync_with_stdio(0);

  int n,m;
  cin>>n>>m;

  TwoEdgeConnectedComponents C(n);
  for(int i=0;i<m;i++){
    int a,b;
    cin>>a>>b;
    C.add_edge(a,b);
  }

  int k=C.build();
  cout<<k<<endl;
  for(int i=0;i<k;i++){
    cout<<C[i].size();
    for(int j=0;j<(int)C[i].size();j++) cout<<" "<<C[i][j];
    cout<<"\n";
  }

  cout<<flush;
  return 0;
}

```
{% endraw %}

<a href="../../../index.html">Back to top page</a>
