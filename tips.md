# TIPS: STL
## 使用初始化列表构造容器对象
```cpp
void example() {
  std::vector<int> int_vector{1, 2, 3, 4};
}
```

## 创建容器时，若知晓容器尺寸，应预留容器尺寸
```cpp
void example() {
  static const std::site_t kFixedStringSize = 100;
  std::vector<std::string> str_vec;
  str_vec.reserve(kFixedStringSize);
}
```

## std::vector
### `emplace_back`优于`push_back`
原因：`emplace_back`会自动构造对象。
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
  obj_vec.emplace_back(TestObj(1));
}
```
