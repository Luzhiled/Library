---
data:
  _extendedDependsOn:
  - icon: ':question:'
    path: tools/chminmax.cpp
    title: tools/chminmax.cpp
  _extendedRequiredBy: []
  _extendedVerifiedWith:
  - icon: ':heavy_check_mark:'
    path: test/aoj/ALDS1_10_C.test.cpp
    title: test/aoj/ALDS1_10_C.test.cpp
  _pathExtension: cpp
  _verificationStatusIcon: ':heavy_check_mark:'
  attributes:
    '*NOT_SPECIAL_COMMENTS*': ''
    links: []
  bundledCode: "Traceback (most recent call last):\n  File \"/opt/hostedtoolcache/Python/3.8.5/x64/lib/python3.8/site-packages/onlinejudge_verify/documentation/build.py\"\
    , line 71, in _render_source_code_stat\n    bundled_code = language.bundle(stat.path,\
    \ basedir=basedir).decode()\n  File \"/opt/hostedtoolcache/Python/3.8.5/x64/lib/python3.8/site-packages/onlinejudge_verify/languages/cplusplus.py\"\
    , line 191, in bundle\n    bundler.update(path)\n  File \"/opt/hostedtoolcache/Python/3.8.5/x64/lib/python3.8/site-packages/onlinejudge_verify/languages/cplusplus_bundle.py\"\
    , line 398, in update\n    raise BundleErrorAt(path, i + 1, \"unable to process\
    \ #include in #if / #ifdef / #ifndef other than include guards\")\nonlinejudge_verify.languages.cplusplus_bundle.BundleErrorAt:\
    \ string/longestcommonsubstring.cpp: line 6: unable to process #include in #if\
    \ / #ifdef / #ifndef other than include guards\n"
  code: "#ifndef call_from_test\n#include<bits/stdc++.h>\nusing namespace std;\n\n\
    #define call_from_test\n#include \"../tools/chminmax.cpp\"\n#undef call_from_test\n\
    \n#endif\n//BEGIN CUT HERE\nint longest_common_substring(string s,string t){\n\
    \  int n=s.size(),m=t.size();\n  s+='$';t+='%';\n  vector< vector<int> > dp(n+2,vector<int>(m+2,-(n+m)));\n\
    \  dp[0][0]=0;\n  for(int i=0;i<=n;i++){\n    for(int j=0;j<=m;j++){\n      chmax(dp[i+1][j],dp[i][j]);\n\
    \      chmax(dp[i][j+1],dp[i][j]);\n      chmax(dp[i+1][j+1],dp[i][j]+(s[i]==t[j]));\n\
    \    }\n  }\n  return dp[n][m];\n}\n//END CUT HERE\n//INSERT ABOVE HERE\n#ifndef\
    \ call_from_test\nsigned main(){\n  return 0;\n}\n#endif\n"
  dependsOn:
  - tools/chminmax.cpp
  isVerificationFile: false
  path: string/longestcommonsubstring.cpp
  requiredBy: []
  timestamp: '2020-03-12 16:36:20+09:00'
  verificationStatus: LIBRARY_ALL_AC
  verifiedWith:
  - test/aoj/ALDS1_10_C.test.cpp
documentation_of: string/longestcommonsubstring.cpp
layout: document
redirect_from:
- /library/string/longestcommonsubstring.cpp
- /library/string/longestcommonsubstring.cpp.html
title: string/longestcommonsubstring.cpp
---