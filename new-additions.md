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
- - size_t count(It p, It q, const T &x)
    Возвращает, сколько раз элемент со значением x входит в последовательность, заданную итераторами p и q.
- - size_t count_if(It p, It q, Pr pred)
    Возвращает, сколько раз предикат pred возвращает значение true. 
- - find(It p, It q, const T &x)
    Возвращает итератор на первое вхождение элемента x в последовательность, заданную итераторами p и q.
- - find_if(It p, It q, Pr pred)
    Возвращает итератор на первый элемент, для которого предикат pred вернул значение true. 
- - transform(It p, It q, Itr out, F func)
    К каждому элементу входящей последовательности применяет функтор func и записывает результат в последовательность,
    начинающуюся с итератора out.
- - sort 
- - - sort(It p, It q), 
- - - sort(It p, It q, Pr pred)
      Сортирует элементы последовательности в порядке возрастания. 
- - - stable_sort(It p, It q), 
- - - stable_sort(It p, It q, Pr pred)
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
    
- -
