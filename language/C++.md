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
class HahaTest : public testing::Test {
public:
    static void SetUpTestCase();
    void SetUp() override;
    void TearDown() override;
}

TEST_F(HahaTest, func1)
{
}
```

```cpp
#include <gtest/gtest_prod.h>
class Haha {
    friend class HahaTest;
    FRIEND_TEST(HahaTest, func1);
};

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MTk2ODk4MTgsNzMzNDI2ODgxLC0xMT
M3MTIzMDc5XX0=
-->