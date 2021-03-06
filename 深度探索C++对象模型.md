## 关于对象

对 C 和 C++ 有一点了解的人，一般会自然地觉得 C++ 消耗的时间空间成本相比 C 更高，实则不然。  

C++ 兼容 struct 的目的，在与使C使用者更好地迁移到 C++ 部落。  

类的内存分布为：
- nonstatic data members
- 对齐
- virtual 额外负担  

派生类隐式包含一个指向基类的指针。（计算内存大小时要计算在内）

指针空间大小为 4 bytes，告诉编译器如何解释特定地址的内容及其大小，强转操作只是改变了编译器解释该指针的长度和内容。
将一个基类指针指向派生类对象，指针得到的是基类大小的空间，相当于派生类被切割了。  

## 构造函数语意学

default constructor在需要的时候被编译器产生出来
四种情况：
- 带有default constructor的member class object
- 带有default constructor 的base class
- 带有一个virtual function的class
- 带有一个virtual base class的class

误解：
- 任何class如果没有定义default constructor，就会被合成出一个来
- 编译器合成出来的default constructor会显式设定“class内每一个data member的默认值”