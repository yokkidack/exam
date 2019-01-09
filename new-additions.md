+ [virtual](http://mycpp.ru/cpp/scpp/cppd_virtual.htm)
+ [virtual, override, final](https://ru.stackoverflow.com/questions/490133/virtual-%D0%B8-override/490144)
+ [инстанцирование](http://www.cyberforum.ru/cpp/thread271621.html)
+ [дичь со спефификацией шаблона](https://habr.com/post/54762/)
+ [assert (оператор проверочного утверждения), static_assert](https://ravesli.com/urok-109-assert-i-static_assert/)
+ [default](https://stackoverflow.com/questions/6502828/what-does-default-mean-after-a-class-function-declaration)
+ [using, typedef, why using is good](https://ru.stackoverflow.com/questions/499481/%D0%9E%D1%82%D0%BB%D0%B8%D1%87%D0%B8%D0%B5-using-%D0%BE%D1%82-typedef)
+ [std::optional but too much, but good about usage](https://habr.com/post/372103/)
+ [std::variant](https://en.cppreference.com/w/cpp/utility/variant)
+ [std::any](https://en.cppreference.com/w/cpp/utility/any)
+ [wtf is string_view](https://habr.com/company/yandex/blog/304510/)
+ [noexept in the bottom](http://qaru.site/questions/20815/when-should-i-really-use-noexcept)
+ [Алгоритмы STL](http://amse.ru/courses/cpp2/2011_03_14.html)
+ [Анонимное namespace](https://ru.stackoverflow.com/questions/490460/%D0%97%D0%B0%D1%87%D0%B5%D0%BC-%D0%BD%D1%83%D0%B6%D0%BD%D0%BE-%D0%BD%D0%B5%D0%B8%D0%BC%D0%B5%D0%BD%D0%BE%D0%B2%D0%B0%D0%BD%D0%BD%D0%BE%D0%B5-%D0%BF%D1%80%D0%BE%D1%81%D1%82%D1%80%D0%B0%D0%BD%D1%81%D1%82%D0%B2%D0%BE-%D0%B8%D0%BC%D0%B5%D0%BD)
    Польза та же, что и при использовании ключевого слова static — избегание проблем с ODR (one definition rule). Если, к примеру, в заголовке у Вас будет int i;, тогда при подключении в 2 и более .cpp файла Вы получите ошибку линковки — один и тот же символ определён дважды. Если же Вы напишете static int i;, то i станет локальным для каждого объектного файла, в который i попадает — т.е. в каждом cpp будет свой i, в отличии от первого варианта, где i один на всю программу. То же самое происходит когда Вы пишите
    ```
    namespace{
        int i;
    }
    ```
i получает внутреннее связывание и, следовательно, проблемы с ODR не будет.

- - size_t `count`(It p, It q, const T &x)
    Возвращает, сколько раз элемент со значением x входит в последовательность, заданную итераторами p и q.
- - size_t `count_if`(It p, It q, Pr pred)
    Возвращает, сколько раз предикат pred возвращает значение true. 
- - `find`(It p, It q, const T &x)
    Возвращает итератор на первое вхождение элемента x в последовательность, заданную итераторами p и q.
- - `find_if`(It p, It q, Pr pred)
    Возвращает итератор на первый элемент, для которого предикат pred вернул значение true. 
- - `transform`(It p, It q, Itr out, F func)
    К каждому элементу входящей последовательности применяет функтор func и записывает результат в последовательность,
    начинающуюся с итератора out.
- - `sort `
- - - `sort`(It p, It q), 
- - - `sort`(It p, It q, Pr pred)
      Сортирует элементы последовательности в порядке возрастания. 
- - - `stable_sort`(It p, It q), 
- - - `stable_sort`(It p, It q, Pr pred)
    Сортирует элементы, сохраняя порядок элементов с одинаковыми значениями относительно друг друга. Эти алгоритмы 
    требуют RA итераторов, поэтому на списке работать не будут. Но `у списка` есть собственные функции члены 
- - - sort, 
- - - stable_sort.
- - [any_of](http://www.cplusplus.com/reference/algorithm/any_of/)
    Returns true if pred returns true for any of the elements in the range [first,last), and false otherwise. 
    If [first,last) is an empty range, the function returns false.
    
```
  template<class InputIterator, class UnaryPredicate>
  bool any_of (InputIterator first, InputIterator last, UnaryPredicate pred)
  {
    while (first!=last) {
      if (pred(*first)) return true;
      ++first;
    }
    return false;
  }
```
- - [all_of](http://www.cplusplus.com/reference/algorithm/all_of/)
    Returns true if pred returns true for all the elements in the range [first,last) or if the range is empty, and false    
    otherwise.
```
// all_of example
#include <iostream>     // std::cout
#include <algorithm>    // std::all_of
#include <array>        // std::array

int main () {
  std::array<int,8> foo = {3,5,7,11,13,17,19,23};

  if ( std::all_of(foo.begin(), foo.end(), [](int i){return i%2;}) )
    std::cout << "All the elements are odd numbers.\n";

  return 0;
}
```
- - [remove_if](http://www.cplusplus.com/reference/algorithm/remove_if/)
Transforms the range [first,last) into a range with all the elements for which pred returns true removed, and returns an iterator to the new end of that range.
```
include <iostream>     // std::cout
#include <algorithm>    // std::remove_if

bool IsOdd (int i) { return ((i%2)==1); }

int main () {
  int myints[] = {1,2,3,4,5,6,7,8,9};            // 1 2 3 4 5 6 7 8 9

  // bounds of range:
  int* pbegin = myints;                          // ^
  int* pend = myints+sizeof(myints)/sizeof(int); // ^                 ^

  pend = std::remove_if (pbegin, pend, IsOdd);   // 2 4 6 8 ? ? ? ? ?
                                                 // ^       ^
  std::cout << "the range contains:";
  for (int* p=pbegin; p!=pend; ++p)
    std::cout << ' ' << *p;
  std::cout << '\n';

  return 0;
}
```
- - [replace_if](http://www.cplusplus.com/reference/algorithm/replace_if/)
    assigns new_value to all the elements in the range [first,last) for which pred returns true.
```
// replace_if example
#include <iostream>     // std::cout
#include <algorithm>    // std::replace_if
#include <vector>       // std::vector

bool IsOdd (int i) { return ((i%2)==1); }

int main () {
  std::vector<int> myvector;

  // set some values:
  for (int i=1; i<10; i++) myvector.push_back(i);               // 1 2 3 4 5 6 7 8 9

  std::replace_if (myvector.begin(), myvector.end(), IsOdd, 0); // 0 2 0 4 0 6 0 8 0

  std::cout << "myvector contains:";
  for (std::vector<int>::iterator it=myvector.begin(); it!=myvector.end(); ++it)
    std::cout << ' ' << *it;
  std::cout << '\n';

  return 0;
}
```
