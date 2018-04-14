
# Metaclasses

## Find the time taken by each method execution


```python
import functools
import types
import time

class Meta(type):
    """
    Meta which decorates all the methods of subclass and it's subclasses if any
    using ``call_handler`` as decorator
    """

    def __new__(mcs, clsname, superclasses, attributedict):
        """Every method gets decorated with ``call_handler``"""
        for attr, attr_val in attributedict.items():
            private = str(attr).replace(f'_{clsname}', '').startswith('__')

            if isinstance(attr_val, types.FunctionType) and not private:
                attributedict[attr] = mcs.call_handler(attr_val)

            elif isinstance(attr_val, staticmethod) and not private:
                attributedict[attr] = staticmethod(mcs.call_handler(attr_val.__func__))

            elif isinstance(attr_val, classmethod) and not private:
                attributedict[attr] = classmethod(mcs.call_handler(attr_val.__func__))

        return type.__new__(mcs, clsname, superclasses, attributedict)

    @staticmethod
    def call_handler(func):
        """Decorator wrapping the functions of class"""
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            # print('Before')
            start = time.time()
            ret_val = func(*args, **kwargs)
            end = time.time()
            # print('After')
            print(f'Total time taken by "{func.__name__}" is {end-start} secs\n')
            return ret_val
        return wrapper


class A(metaclass=Meta):

    def instance_method(self):
        print('Instance method', self)
        time.sleep(3)

    @staticmethod
    def static_method():
        print('Static method')
        time.sleep(1)

    @classmethod
    def class_method(cls):
        print('Class method', cls)
        time.sleep(2)

    def _private_method(self):
        print('Conventionally private method')
        time.sleep(0.5)

    def __super_private_method(self):
        print('Super private method')
        time.sleep(2)

obj_a = A()
obj_a.instance_method()
obj_a.static_method()
obj_a.class_method()
obj_a._private_method()
obj_a._A__super_private_method()  # This is not decorated intentionally

```

    Instance method <__main__.A object at 0x104d1b470>
    Total time taken by "instance_method" is 3.004960060119629 secs
    
    Static method
    Total time taken by "static_method" is 1.0046379566192627 secs
    
    Class method <class '__main__.A'>
    Total time taken by "class_method" is 2.004424810409546 secs
    
    Conventionally private method
    Total time taken by "_private_method" is 0.5022380352020264 secs
    
    Super private method



```python

```
