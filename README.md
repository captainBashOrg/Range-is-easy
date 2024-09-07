print("Range - это просто")

class StepValueError (ValueError):
    pass

class Iterator:
    """
start - целое число с которого начинается итерация.
stop - целое число на котором заканчивается итерация.
step - шаг с которой совершается итерация.
pointer - указывает на текущее число в итерации (изначально start)
    """
    def __init__(self, start, stop, step=1):
        if step == 0:
            raise StepValueError('шаг не может быть равен 0')
        else:
            self.__name__ = "Iterator"
            self.start =start
            self.stop = stop
            self.step = step
            self.pointer = start # при создании указатель == начальному значению


    def __iter__(self):
        self.pointer = self.start
        return self

    def __next__(self):
        if (self.step > 0 and self.pointer > self.stop) or (self.step < 0 and self.pointer < self.stop):
            raise StopIteration
        p = self.pointer
        self.pointer += self.step
        return p

#    def __call__(self):
#        print(self.__name__z)

#Пример выполняемого кода:
try:
    iter1 = Iterator(100, 200, 0)
    for i in iter1:
        print(i, end=' ')
except StepValueError:
    print('Шаг указан неверно')

iter2 = Iterator( -5, 1, 1)
iter3 = Iterator(6, 15, 2)
iter4 = Iterator(5, 1, -1)
iter5 = Iterator(10, 1)


for i in iter2:
    print(i, end=' ')
print()
for i in iter3:
    print(i, end=' ')
print()
for i in iter4:
    print(i, end=' ')
print()
for i in iter5:
    print(i, end=' ')
print()
