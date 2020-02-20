# disable debug message

```cpp
#ifndef NULLSTREAM_H
#define NULLSTREAM_H

#include <iosfwd>
using namespace std;

class NullStream
{
  public:
    NullStream() { }

    /// swallow all types
    template<typename T>
    NullStream& operator<<(T const&) { return *this; }

    /// swallow manipulator templates; ex. endl
    NullStream& operator<<(ostream&(ostream&)) { return *this; }
};

// #define cout NullStream()
// #define printf(format, ...) ;

#endif //NULLSTREAM_H

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMzcxMjMwNzldfQ==
-->