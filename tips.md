## TIPS: final关键字
### 修饰类以禁止继承
```cpp
class Example final : Base {
};
```
Example类不可继承。

## TIPS: STL容器
### 使用初始化列表构造容器对象
```cpp
void example() {
  std::vector<int> int_vector{1, 2, 3, 4};
}
```

### std::vector
#### emplace_back优于push_back
原因：emplace_back会自动构造对象。
```cpp
class TestObj {
 public:
  TestObj(int val) : val_(val) {}
 private:
  int val_;
};

void example() {
  std::vector<TestObj> obj_vec;
  obj_vec.emplace_back(1);
  obj_vec.push_back(TestObj(1));
}
```

#### 创建已知尺寸的vector时，应预留容量
```cpp
void example() {
  constexpr std::site_t kFixedStringSize = 100;
  std::vector<std::string> str_vec;
  str_vec.reserve(kFixedStringSize);
}
```
