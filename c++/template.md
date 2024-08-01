（智谱清言，2024.8.1）



C++模板是一种强大的特性，它允许编写与数据类型无关的代码。模板提供了代码复用的机制，使得可以创建通用的函数或类，这些函数或类可以用于任何数据类型。C++模板分为两种：函数模板和类模板。



### 函数模板

函数模板是一系列相关函数的蓝图，这些函数的参数类型和返回类型可以不同，但函数体是相同的。下面是一个函数模板的例子：

```c
template <typename T>
T max(T a, T b) {
    return (a > b) ? a : b;
}

```

在这个例子中，`T` 是一个占位符，它可以在调用函数时被任何类型所替换。以下是如何使用这个函数模板：

```c
int main() {
    int i = 5, j = 6;
    double x = 5.5, y = 6.5;
    
    int maxInt = max(i, j);  // 调用 max<int>
    double maxDouble = max(x, y);  // 调用 max<double>
    
    return 0;
}

```





### 类模板

类模板允许创建一个可以用于任何数据类型的类。下面是一个类模板的例子：

```c
template <typename T>
class Array {
private:
    T* data;
    int size;
public:
    Array(T arr[], int s);
    T getMax();
};

template <typename T>
Array<T>::Array(T arr[], int s) {
    size = s;
    data = new T[size];
    for (int i = 0; i < size; i++) {
        data[i] = arr[i];
    }
}

template <typename T>
T Array<T>::getMax() {
    T max = data[0];
    for (int i = 1; i < size; i++) {
        if (data[i] > max) {
            max = data[i];
        }
    }
    return max;
}

```

以下是如何使用这个类模板：

```c
int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    Array<int> intArray(arr, 5);
    cout << "Max integer: " << intArray.getMax() << endl;
    
    double arrDouble[3] = {1.1, 2.2, 3.3};
    Array<double> doubleArray(arrDouble, 3);
    cout << "Max double: " << doubleArray.getMax() << endl;
    
    return 0;
}

```

在这个例子中，`Array` 类被定义为可以处理任何类型的数组，并且能够找到数组中的最大值。通过类模板，我们可以避免为每种数据类型编写重复的代码。
