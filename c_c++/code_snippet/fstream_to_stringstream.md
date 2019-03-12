# fstream_to_stringstream

```c++
// #include <algorithm>
// #include <sstream>
// #include <fstream>

std::ifstream fin("main.cpp");
std::ostringstream sout;
std::copy(std::istreambuf_iterator<char>(fin),
     std::istreambuf_iterator<char>(),
     std::ostreambuf_iterator<char>(sout));
```