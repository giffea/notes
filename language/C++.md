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

# google test
```cpp
#include <gtest/gtest.h>
class Haha_test : public testing::Test {
public:
    static void SetUpTestCase();
    void SetUp() override;
    void TearDown() override;
}

TEST_F(Haha_test, func1){
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzNTA5ODc0MDksLTExMzcxMjMwNzldfQ
==
-->