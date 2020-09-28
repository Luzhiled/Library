---
data:
  _extendedDependsOn:
  - icon: ':heavy_check_mark:'
    path: string/suffixarray.cpp
    title: string/suffixarray.cpp
  _extendedRequiredBy: []
  _extendedVerifiedWith:
  - icon: ':heavy_check_mark:'
    path: test/aoj/2711.test.cpp
    title: test/aoj/2711.test.cpp
  - icon: ':heavy_check_mark:'
    path: test/aoj/3063.test.cpp
    title: test/aoj/3063.test.cpp
  - icon: ':heavy_check_mark:'
    path: test/aoj/3112.test.cpp
    title: test/aoj/3112.test.cpp
  - icon: ':heavy_check_mark:'
    path: test/yosupo/number_of_substrings.test.cpp
    title: test/yosupo/number_of_substrings.test.cpp
  _pathExtension: cpp
  _verificationStatusIcon: ':heavy_check_mark:'
  attributes:
    links: []
  bundledCode: "Traceback (most recent call last):\n  File \"/opt/hostedtoolcache/Python/3.8.5/x64/lib/python3.8/site-packages/onlinejudge_verify/documentation/build.py\"\
    , line 71, in _render_source_code_stat\n    bundled_code = language.bundle(stat.path,\
    \ basedir=basedir).decode()\n  File \"/opt/hostedtoolcache/Python/3.8.5/x64/lib/python3.8/site-packages/onlinejudge_verify/languages/cplusplus.py\"\
    , line 191, in bundle\n    bundler.update(path)\n  File \"/opt/hostedtoolcache/Python/3.8.5/x64/lib/python3.8/site-packages/onlinejudge_verify/languages/cplusplus_bundle.py\"\
    , line 398, in update\n    raise BundleErrorAt(path, i + 1, \"unable to process\
    \ #include in #if / #ifdef / #ifndef other than include guards\")\nonlinejudge_verify.languages.cplusplus_bundle.BundleErrorAt:\
    \ string/longestcommonprefix.cpp: line 6: unable to process #include in #if /\
    \ #ifdef / #ifndef other than include guards\n"
  code: "#ifndef call_from_test\n#include<bits/stdc++.h>\nusing namespace std;\n\n\
    #define call_from_test\n#include \"suffixarray.cpp\"\n#undef call_from_test\n\n\
    #endif\n//BEGIN CUT HERE\nstruct LongestCommonPrefix{\n  SuffixArray sa;\n\n \
    \ vector<int> ht;\n  vector< vector<int> > dat;\n  LongestCommonPrefix(string\
    \ &s):sa(s){\n    int n=s.size();\n    vector<int> lcp(n,0);\n\n    int t=0;\n\
    \    lcp[0]=0;\n    for(int i=0;i<n;i++){\n      int j=sa[sa.rev[i]-1];\n    \
    \  if(t>0) t--;\n      for(;j+t<n&&i+t<n;t++){\n        if(sa.s[j+t]!=sa.s[i+t])\
    \ break;\n      }\n      lcp[sa.rev[i]-1]=t;\n    }\n\n    int h=1;\n    while((1<<h)<n)\
    \ h++;\n    dat.assign(h,vector<int>(n));\n    ht.assign(n+1,0);\n    for(int\
    \ j=2;j<=n;j++) ht[j]=ht[j>>1]+1;\n\n    for(int j=0;j<n;j++) dat[0][j]=lcp[j];\n\
    \    for(int i=1,p=1;i<h;i++,p<<=1)\n      for(int j=0;j<n;j++)\n        dat[i][j]=min(dat[i-1][j],dat[i-1][min(j+p,n-1)]);\n\
    \  }\n\n  // a, b are indices for suffix array\n  int query(int a,int b){\n  \
    \  assert(a!=b);\n    if(a>b) swap(a,b);\n    int l=b-a;\n    return min(dat[ht[l]][a],dat[ht[l]][b-(1<<ht[l])]);\n\
    \  }\n\n  // a, b are indices for string\n  int lcp(int a,int b){\n    return\
    \ query(sa.rev[a],sa.rev[b]);\n  }\n};\n//END CUT HERE\n#ifndef call_from_test\n\
    //INSERT ABOVE HERE\nsigned main(){\n  return 0;\n};\n#endif\n"
  dependsOn:
  - string/suffixarray.cpp
  isVerificationFile: false
  path: string/longestcommonprefix.cpp
  requiredBy: []
  timestamp: '2019-12-26 23:22:59+09:00'
  verificationStatus: LIBRARY_ALL_AC
  verifiedWith:
  - test/aoj/3063.test.cpp
  - test/aoj/2711.test.cpp
  - test/aoj/3112.test.cpp
  - test/yosupo/number_of_substrings.test.cpp
documentation_of: string/longestcommonprefix.cpp
layout: document
redirect_from:
- /library/string/longestcommonprefix.cpp
- /library/string/longestcommonprefix.cpp.html
title: string/longestcommonprefix.cpp
---