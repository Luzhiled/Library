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


# :heavy_check_mark: test/aoj/GRL_5_E.linkcuttree.test.cpp

<a href="../../../index.html">Back to top page</a>

* <a href="{{ site.github.repository_url }}/blob/master/test/aoj/GRL_5_E.linkcuttree.test.cpp">View this file on GitHub</a>
    - Last commit date: 2019-12-27 09:39:50+09:00


* see: <a href="http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=GRL_5_E">http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=GRL_5_E</a>


## Depends on

* :heavy_check_mark: <a href="../../../library/linkcuttree/base.cpp.html">linkcuttree/base.cpp</a>
* :heavy_check_mark: <a href="../../../library/linkcuttree/path.cpp.html">linkcuttree/path.cpp</a>
* :heavy_check_mark: <a href="../../../library/tools/fastio.cpp.html">tools/fastio.cpp</a>


## Code

<a id="unbundled"></a>
{% raw %}
```cpp
#define PROBLEM "http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=GRL_5_E"

#include<bits/stdc++.h>
using namespace std;

#define call_from_test
#include "../../tools/fastio.cpp"
#include "../../linkcuttree/base.cpp"
#include "../../linkcuttree/path.cpp"
#undef call_from_test

signed main(){
  using ll = long long;

  int n;
  cin>>n;

  using P = pair<ll, ll>;
  using Node = NodeBase<P, ll>;
  constexpr size_t LIM = 1e6;
  using LCT = Path<Node, LIM>;

  auto f=[](P a,P b){return P(a.first+b.first,a.second+b.second);};
  auto g=[](P a,int b){return P(a.first+b*a.second,a.second);};
  auto h=[](ll a,ll b){return a+b;};
  LCT lct(f,g,h,P(0,0),0);

  for(int i=0;i<n;i++) lct.create(P(0,1));
  for(int i=0;i<n;i++){
    int k;
    cin>>k;
    for(int j=0;j<k;j++){
      int c;
      cin>>c;
      lct.link(lct[i],lct[c]);
    }
  }

  int q;
  cin>>q;
  ll sum=0;
  for(int i=0;i<q;i++){
    int t;
    cin>>t;
    if(t==0){
      int a,b;
      cin>>a>>b;
      lct.update(lct[a],b);
      sum+=b;
    }
    if(t==1){
      int a;
      cin>>a;
      cout<<lct.query(lct[a]).first-sum<<"\n";
    }
  }
  cout<<flush;
  return 0;
}

```
{% endraw %}

<a id="bundled"></a>
{% raw %}
```cpp
Traceback (most recent call last):
  File "/opt/hostedtoolcache/Python/3.8.0/x64/lib/python3.8/site-packages/onlinejudge_verify/docs.py", line 340, in write_contents
    bundler.update(self.file_class.file_path)
  File "/opt/hostedtoolcache/Python/3.8.0/x64/lib/python3.8/site-packages/onlinejudge_verify/bundle.py", line 154, in update
    self.update(self._resolve(included, included_from=path))
  File "/opt/hostedtoolcache/Python/3.8.0/x64/lib/python3.8/site-packages/onlinejudge_verify/bundle.py", line 123, in update
    raise BundleError(path, i + 1, "found codes out of include guard")
onlinejudge_verify.bundle.BundleError: tools/fastio.cpp: line 5: found codes out of include guard

```
{% endraw %}

<a href="../../../index.html">Back to top page</a>
