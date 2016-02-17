# LINK_DIRECTORIES

cmakeでは、`LINK_DIRECTORIES`マクロによって、ライブラリへのパスを指定できる(`-L`オプション)が、
これはうまく動かないことが多い。
なので、`TARGET_LINK_LIBRARIES`によって絶対パスを指定するのが推薦方法。
