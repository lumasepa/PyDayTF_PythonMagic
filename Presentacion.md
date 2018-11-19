<!-- $theme: default -->

# Python Magic

---

# repr(self)

```python
>>> from Tenerife import Sergio
>>> Sergio.full_name()
"Sergio Medina Toledo"
>>> Sergio.work()
["VoIP", "Django", "Microservices", "Scalability", "DevOps"]
>>> Sergio.others()
["Linux", "Security", "Architectures", "AsyncIO", "Embedded"]
>>> Sergio.languages()
["Python", "C", "C++", "Rust", "Go", "Java", "js"]
>>> Sergio.job()
<DevOps at Sedicii>
>>>  
```

---

# `def Index():`

```python
{
    "Magic Methods",
    "Introspection",
    "Runtime Class Declaration",
    "Metaclasses",
}
```

---

# `def MagicMethods():`

* Son métodos especiales que puedes definir para añadir magia a tus clases.
* El interprete de python quita el "azucar" al lenguaje y eso se traduce en llamar a los magic methods.
* Es una forma elegante de jugar con python.
* Se definen en los PEPs y empiezan con __ y terminan con ___
* Tambien se les conoce como `double-underscore methods`, `dunder methods`, `"feature" protocol`
* Algunos los usais a diario, `def __init__(self):`

---

# `with sugar():`

```python
faya = Tree(kind="Faya")
faya.age = 10 + 2
print(faya.kind)
faya[""]
faya in laurisilva
faya("", 1)
faya == laurisilva
```

---

# `with out(sugar()):`

```python
faya = Tree.__new__(Tree)
faya.__init__(kind="Faya")
faya.__setattr__("age", 10.__add__(2))
print(faya.__getattribute__("kind"))
faya.__getitem__("")
laurisilva.__contains__(faya)
faya.__call__("", 1)
faya.__eq__(laurisilva)
```

---

# It's Magic !!

![Magic](./magic.gif)

---

# `MagicMethods.class.building()`

```python
>>> MagicMethods.class.building()
{
    "__new__(cls, [...])": ["Faya()" "Build Instance"],
    "__init__(self, [...])": ["Faya()", "Initializes Instance"],
    "__del__(self)": ["del obj", "Destroy Instance"]
}
```

---

# `Example(MagicMethods.class.building())`

```python
class Singleton: 

    _instance = None

    def __new__(cls, *args, **kwargs):
        if not cls._instance:
            cls._instance = super(Singleton, cls).__new__(*args, **kwargs)
        return cls._instance
```

---

# `MagicMethods.comparasion()`

```python
>>> MagicMethods.comparasion()
{
    "__cmp__(self, other)": ["self == other", "self < other", "self > other"],
    "__eq__(self, other)": "self == other",
    "__ne__(self, other)": "self != other",
    "__lt__(self, other)": "self < other",
    "__gt__(self, other)": "self > other",
    "__le__(self, other)": "self <= other",
    "__ge__(self, other)": "self >= other"
}
```

---

# `MagicMethods.numeric.unary()`

```python
>>> MagicMethods.numeric.unary()
{
    "__pos__(self)": "+obj",
    "__neg__(self)": "-obj",
    "__abs__(self)": "abs(obj)",
    "__invert__(self)": "~obj",
    "__round__(self, n)": "round(obj, 2)",
    "__floor__(self)": "math.floor(obj)",
    "__ceil__(self)": "math.ceil(obj)",
    "__trunc__(self)": "math.trunc()"
}
```

---

# `MagicMethods.numeric.binary()`

```python
>>> MagicMethods.numeric.binary()
{
    "__add__(self, other)": "self + other",
    "__sub__(self, other)": "self - other",
    "__mul__(self, other)": "self * other",
    "__floordiv__(self, other)": "self // other",
    "__div__(self, other)": "self / other",
    "__mod__(self, other)": "self % other",
    "__pow__(self, other)": "self ** other",
    "__lshift__(self, other)": "self << other",
    "__rshift__(self, other)": "self >> other",
    "__and__(self, other)": "self & other",
    "__or__(self, other)": "self | other",
    "__xor__(self, other)": "self ^ other",
}
```

---

# `MagicMethods.numeric.reflected.binary()`

```python
>>> MagicMethods.numeric.reflected.binary()
{
    "__radd__(self, other)": "other + self",
    "__rsub__(self, other)": "other - self",
    "__rmul__(self, other)": "other * self",
    "__rfloordiv__(self, other)": "other // self",
    "__rdiv__(self, other)": "other / self",
    "__rmod__(self, other)": "other % self",
    "__rpow__(self, other)": "other ** self",
    "__rlshift__(self, other)": "other << self",
    "__rrshift__(self, other)": "other >> self",
    "__rand__(self, other)": "other & self",
    "__ror__(self, other)": "other | self",
    "__rxor__(self, other)": "other ^ self",
}
```

---

# `MagicMethods.augmented.assignment()`

```python
>>> MagicMethods.augmented.assignment()
{
    "__iadd__(self, other)": "self += other",
    "__isub__(self, other)": "self -= other",
    "__imul__(self, other)": "self *= other",
    "__ifloordiv__(self, other)": "self //= other",
    "__idiv__(self, other)": "self /= other",
    "__imod__(self, other)": "self %= other",
    "__ipow__(self, other)": "self **= other",
    "__ilshift__(self, other)": "self <<= other",
    "__irshift__(self, other)": "self >>= other",
    "__iand__(self, other)": "self &= other",
    "__ior__(self, other)": "self |= other",
    "__ixor__(self, other)": "self ^= other",
}
```

---

# `MagicMethods.type.conversion()`

```python
>>> MagicMethods.type.conversion()
{
    "__int__(self)": "int(self)",
    "__float__(self)": "float(self)",
    "__complex__(self, n)": "complex(self, n)",
    "__oct__(self)": "oct(self)",
    "__hex__(self)": "hex(self)",
    "__trunc__(self)": "math.trunc(self)",
}
```

---

# `MagicMethods.copying()`
```python
{
    "__copy__(self)": "copy.copy(self)"
    "__deepcopy__(self, memodict={})": "copy.deepcopy(self)"
}
```

---

# `MagicMethods.class.representation()`

```python
>>> MagicMethods.class.representation()
{
    "__str__(self)": "str(self)",
    "__repr__(self)": "repr(self)",
    "__unicode__(self)": "unicode(self)",
    "__format__(self, formatstr)": "'{:formatstr}'.format(self)",
    "__hash__(self)": "hash(self)",
    "__nonzero__(self)": "bool(self)",
    "__dir__(self)": "dir(self)",
    "__sizeof__(self)": "sys.getsizeof(self)",
}
```

---

# `MagicMethods.class.attribute.access()`

```python
>>> MagicMethods.class.attribute.access()
{
    "__getattr__(self, name)": ["self.name", "getattr(self, 'name')"] # name is not an attr of self
    "__setattr__(self, name, value)": ["self.name = value", "setattr(self, 'name', value)"]
    "__delattr__(self, name)": ["del self.name", "delattr(self, 'name')"]
    "__getattribute__(self, name)": ["self.name", "getattr(self, 'name')"] # name may be an attr of self
}
```

---

# `Example(MagicMethods.class.attribute.access())`

```python

class LoggedMethodProxy(object):
    """
    Proxy pattern used to log object method calls and result
    """

    def __init__(self, obj):
        self._obj = obj

    def __getattr__(self, item):
        item_obj = getattr(self._obj, item)
        if type(item_obj) == MethodType:
            if asyncio.iscoroutinefunction(item_obj):
                async def proxy_fn(*args, **kwargs):
                    result = await item_obj(*args, **kwargs)
                    logger.debug(f"Called async {item} args: {args}, kwargs: {kwargs}, result: {result}.")
                    return result
            else:
                def proxy_fn(*args, **kwargs):
                    result = item_obj(*args, **kwargs)
                    logger.debug(f"Called {item} args: {args}, kwargs: {kwargs}, result: {result}.")
                    return result

            return proxy_fn
        return item_obj

```

---

# `MagicMethods.containers()`

```python
>>> MagicMethods.containers()
{
    "__len__(self)": "len(self)",
    "__getitem__(self, key)": "self[key]",
    "__setitem__(self, key, value)": "self[key] = value",
    "__delitem__(self, key)": "del self[key]",
    "__iter__(self)": ["iter(self)", "for _ in self"],
    "__next__(self)": ["next(self)", "for _ in self"],
    "__reversed__(self)": "reversed(self)",
    "__contains__(self, item)": "item in self",
    "__missing__(self, key)": "self[key]", # key does not exist in self
}
```

---

# `WithoutSugar(MagicMethods.containers())`

```python
for i in numbers:
    BLOCK

iterator = numbers.__iter__()
try:
    while True:
        i = iterator.__next__()
        BLOCK
except StopIteration:
    pass
except Exception as e:
    raise e
```

---

# `Example(MagicMethods.containers())`

```python
class SubscriptableClass:

    def __getitem__(self, key):
        return getattr(self, key)
        
    def __setitem__(self, key, value):
        return setattr(self, key, value)

    def __delitem__(self, key):
        return delattr(self, key)

```

---

# `MagicMethods.class.callable()`

```python
>>> MagicMethods.class.callable()
{
    "__call__(self, *args, **kwargs)": "self(*args, **kwargs)"
}
```

---

# `Example(MagicMethods.class.callable())`

```python
class Script(object):
    """
    Redis script abstraction, with caching support
    """

    def __init__(self, name, script):
        self.script = script
        self.name = name
        self.script_sha1 = sha1(
            self.script
        ).hexdigest()

    async def _load_script(self):
        """
        Loads the script in redis for caching

        :return:
        """
        await client.script_load(self.script)

    async def _run_script(self, keys, args):
        """
        Runs the script

        :param keys: keys for the script KEYS global variable
        :param args: args for the script ARGV global variable
        :return:
        """
        result = await client.evalsha(
            digest=self.script_sha1,
            keys=keys,
            args=args,
        )
        return result

    async def __call__(self, keys=None, args=None):
        """
        Run the script caching if it isn't cached

        :param keys: keys for the script KEYS global variable
        :param args: args for the script ARGV global variable
        :return:
        """
        if args is None:
            args = []
        if keys is None:
            keys = []
        try:
            result = await self._run_script(keys, args)
        except aioredis.errors.ReplyError as e:
            if "NOSCRIPT" in str(e):
                await self._load_script()
                result = await self._run_script(keys, args)
            else:  # pragma: no cover
                raise e
        return result

redis_client.my_script = Script("my_script", "redis lua script")
```

---

# `MagicMethods.context_managers()`

```python
>>> MagicMethods.context_managers()
{
    "__enter__(self)": "with self",
    "__exit__(self, exception_type, exception_value, traceback)": "with self",
    "__aenter___(self)": "async with self",
    "__aexit__(self, exception_type, exception_value, traceback)": "async with",
}
```

---

# `WithoutSugar(MagicMethods.context_managers())`


```python
with ctx_mgr as VAR:
    BLOCK

value = ctx_mgr.__enter__(ctx_mgr)
exc = False
try:
    try:
        VAR = value  # Only if "as VAR" is present
        BLOCK
    except:
        # The exceptional case is handled here
        exc = True
        if not ctx_mgr.__exit__(*sys.exc_info()):
            raise
        # The exception is swallowed if exit() returns true
finally:
    # The normal and non-local-goto cases are handled here
    if not exc:
        ctx_mgr.__exit__(mgr, None, None, None)
```

---

# `Example(MagicMethods.context_managers())`

```python
class TimeMeter(Meter):
    def __init__(self, *args, **kwargs):
        super().__init__(*args, **kwargs)
        self.time_start = None

    def start(self):
        self.time_start = time.time()

    def stop(self):
        time_end = time.time()
        self.value = time_end - self.time_start

    def __enter__(self):
        self.start()
        return self

    def __exit__(self, exc_type, exc_val, exc_tb):
        self.stop()

with TimeMeter("db.query.users"):
    pass
```

---

# `MagicMethods.decriptor.objects()`

```python
>>> MagicMethods.decriptor.objects()
{
    "__get__(self, instance, cls)": ["instance.self", "cls.self"],
    "__set__(self, instance, value)": "instance.self = value",
    "__delete__(self, instance)": "del instance.self",
}
```

---

# `Example(MagicMethods.decriptor.objects())`

```python
class FieldDescriptor(object):
    def __init__(self, field_name):
        self.field_name = field_name

    def __get__(self, instance, cls):
        if instance is not None:
            return instance._data.get(self.field_name)
        else:
            return cls.meta.get_field(self.field_name)

    def __set__(self, instance, value):
        instance._data[self.field_name] = value

class Node(Model):
    identifier = UUIDField(primary_key=True)
    status = CharField(max_length=100)
```

---

# `def Introspection()`

* Introspección es la habilidad de un programa de examinar el tipo o atributos de un objeto en runtime.
* `cls = type(obj)`, para determinar el tipo de un objeto.
* builtin `getattr(obj, attr)`, para obtener attributos de un objeto.
* builtin `setattr(obj, attr, value)`, para setear attributos de un objeto.
* builtin `delattr(obj, attr)`, para eliminar attributos de un objeto.
* builtin `hasattr(obj, attr)`, para examinar attributos de un objeto.
* modulo `inspect`, introspeccion avanzada.

---

# `Example(Introspection())`

```python
def args2kwargs(fn):

    @functools.wraps(fn)
    def wrapper(*args, **kwargs):
        args_fn = inspect.getfullargspec(fn)[0]
        kwargs["all_args"] =  {
            **kwargs,
            **dict(zip(args_fn, args))
        }
        return fn(*args, **kwargs)

    return wrapper
```

---

# `def RuntimeClassDeclaration()`

* Crear un nuevo tipo/clase dinamicamente
* Posibles usos:
    - Crear clases nuevas a partir de una configuracion externa (swagger)
    - Crear clases nuevas a partir de otras clases para añadir funcionalidad
    - Crear clases nuevas en base a una documentacion de un api

```python 
cls = type(classname, superclasses, attributes_dict)
```

---

# `def Metaclass()`

* Clase usada para construir otra case
* Evita problemas de clase hija sobreescribiendo `__new__`
* Uso : `class Klass(metaclass=MetaClass)`

---

# `Example(Metaclass())`

```python
class Singleton(type):
    _instances = {}

    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            cls._instances[cls] = super(Singleton, cls).__call__(*args, **kwargs)
        return cls._instances[cls]

def DBPool(metaclass=Singleton):
    pass
```

---

## `Example(RuntimeClassDeclaration() + Metaclasses())`

```python

class ModelBaseMetaClass(type):
    def __new__(mcs, *args, **kwargs):
        model_class = type.__new__(mcs, *args, **kwargs)
        pk = None

        # get all field of the model
        fields = {k: v for k, v in model_class.__dict__.items() if isinstance(v, Field)}

        # get if there is a pk and set the name for each field
        for field_name, field_value in fields.items():
            field_value.name = field_name
            if field_value.primary_key:
                pk = field_value

        # Add a pk if does not exist
        if pk is None:
            model_class.pk = PrimaryKeyField()
            model_class.pk.name = "pk"
            fields["pk"] = model_class.pk

        # change fields for FieldsDescriptors for access in class instance to values
        for field_name, field_value in fields.items():
            setattr(model_class, field_name, FieldDescriptor(field_name))

        # Add the meta obj to the class
        assert issubclass(model_class.Meta, MetaBase), "Meta class of Model have to inherit from MetaBase"
        model_class.meta = model_class.Meta(model_class, fields)

        # Add the objects obj to the class
        model_class.objects = type(
            "{}Manager".format(model_class.__name__),
            (ModelManager,),
            {"model": model_class}
        )()

        return model_class

class Model(metaclass=ModelBaseMetaClass):
     class Meta(MetaBase):
        pass

class Node(Model):
    identifier = UUIDField(primary_key=True)
    status = CharField(max_length=100)
```

---

# Conclusiones

* Python es un lenguaje muy versatil con el que se puede hacer muchos tipos de magias.
* Un gran poder conlleva una gran responsabilidad
* Tenemos un toolbox que podemos usar en la proxima libreria que escribamos.

---

# Agradecimientos

* A todos los asistentes
* Organización del pyday
* Patrocinadores

---

# ¿Preguntas?
