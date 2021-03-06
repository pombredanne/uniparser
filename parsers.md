## CSSParser (css)

```
CSS selector parser, requires `bs4` and `lxml`(optional).
    Since HTML input object always should be string, _RECURSION_LIST will be True.

    Parse the input object with standard css selector, features from `BeautifulSoup`.

        :param input_object: input object, could be Tag or str.
        :type input_object: [Tag, str]
        :param param: css selector path
        :type param: [str]
        :param value: operation for each item of result
        :type value: [str]

            @attribute: return element.get(xxx)

            $text: return element.text

            $innerHTML, $html: return element.decode_contents()

            $outerHTML, $string: return str(element)

            $self: return element

        :return: list of Tag / str
        :rtype: List[Union[str, Tag]]

        examples:

            ['<a class="url" href="/">title</a>', 'a.url', '@href']      => ['/']
            ['<a class="url" href="/">title</a>', 'a.url', '$text']      => ['title']
            ['<a class="url" href="/">title</a>', 'a.url', '$innerHTML'] => ['title']
            ['<a class="url" href="/">title</a>', 'a.url', '$html']      => ['title']
            ['<a class="url" href="/">title</a>', 'a.url', '$outerHTML'] => ['<a class="url" href="/">title</a>']
            ['<a class="url" href="/">title</a>', 'a.url', '$string']    => ['<a class="url" href="/">title</a>']
            ['<a class="url" href="/">title</a>', 'a.url', '$self']      => [<a class="url" href="/">title</a>]

            WARNING: $self returns the original Tag object
    

valid value args: ['@attr', '$text', '$innerHTML', '$html', '$outerHTML', '$string', '$self']

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors

https://github.com/ClericPy/uniparser
```
## CSSSingleParser (css1)

```
Similar to CSSParser but use select_one instead of select method.
        examples:

            ['<a class="url" href="/">title</a>', 'a.url1', '@href']      => None
            ['<a class="url" href="/">title</a>', 'a.url', '@href']      => '/'
            ['<a class="url" href="/">title</a>', 'a.url', '$text']      => 'title'
            ['<a class="url" href="/">title</a>', 'a.url', '$innerHTML'] => 'title'
            ['<a class="url" href="/">title</a>', 'a.url', '$html']      => 'title'
            ['<a class="url" href="/">title</a>', 'a.url', '$outerHTML'] => '<a class="url" href="/">title</a>'
            ['<a class="url" href="/">title</a>', 'a.url', '$string']    => '<a class="url" href="/">title</a>'
            ['<a class="url" href="/">title</a>', 'a.url', '$self']      => <a class="url" href="/">title</a>
    

valid value args: ['@attr', '$text', '$innerHTML', '$html', '$outerHTML', '$string', '$self']

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors

https://github.com/ClericPy/uniparser
```
## SelectolaxParser (selectolax)

```
CSS selector parser based on `selectolax`, faster than lxml.
    Since HTML input object always should be string, _RECURSION_LIST will be True.

    Parse the input object with standard css selector.

        :param input_object: input object, could be Node or str.
        :type input_object: [Node, str]
        :param param: css selector path
        :type param: [str]
        :param value: operation for each item of result
        :type value: [str]

            @attribute: return element.attributes.get(xxx)

            $text: return element.text

            $outerHTML, $html: return element.html

            $self: return element

        :return: list of Node / str
        :rtype: List[Union[str, Node]]

        examples:

            ['<a class="url" href="/">title</a>', 'a.url', '@href']      => ['/']
            ['<a class="url" href="/">title</a>', 'a.url', '$text']      => ['title']
            ['<a class="url" href="/">title</a>', 'a.url', '$html']      => ['<a class="url" href="/">title</a>']
            ['<a class="url" href="/">title</a>', 'a.url', '$outerHTML'] => ['<a class="url" href="/">title</a>']
            ['<a class="url" href="/">title</a>', 'a.url', '$self']      => [<a class="url" href="/">title</a>]

            WARNING: $self returns the original Node object
    

valid value args: ['@attr', '$text', '$html', '$outerHTML', '$self']

https://github.com/rushter/selectolax

https://github.com/ClericPy/uniparser
```
## SelectolaxSingleParser (se1)

```
Similar to SelectolaxParser but use css_first instead of select method.
        examples:

            ['<a class="url" href="/">title</a>', 'a.url1', '@href']      => None
            ['<a class="url" href="/">title</a>', 'a.url', '@href']      => '/'
            ['<a class="url" href="/">title</a>', 'a.url', '$text']      => 'title'
            ['<a class="url" href="/">title</a>', 'a.url', '$innerHTML'] => 'title'
            ['<a class="url" href="/">title</a>', 'a.url', '$html']      => 'title'
            ['<a class="url" href="/">title</a>', 'a.url', '$outerHTML'] => '<a class="url" href="/">title</a>'
            ['<a class="url" href="/">title</a>', 'a.url', '$string']    => '<a class="url" href="/">title</a>'
            ['<a class="url" href="/">title</a>', 'a.url', '$self']      => <a class="url" href="/">title</a>
    

valid value args: ['@attr', '$text', '$html', '$outerHTML', '$self']

https://github.com/rushter/selectolax

https://github.com/ClericPy/uniparser
```
## XMLParser (xml)

```
XML parser, requires `bs4` and `lxml`(necessary), but not support `xpath` for now.
    Since XML input object always should be string, _RECURSION_LIST will be True.

    Parse the input object with css selector, `BeautifulSoup` with features='xml'.

        :param input_object: input object, could be Tag or str.
        :type input_object: [Tag, str]
        :param param: css selector path
        :type param: [str]
        :param value: operation for each item of result
        :type value: [str]

            @attribute: return element.get(xxx)

            $text: return element.text

            $innerXML: return element.decode_contents()

            $outerXML: return str(element)

            $self: return element

        :return: list of Tag / str
        :rtype: List[Union[str, Tag]]

        examples:

            ['<dc:creator><![CDATA[author]]></dc:creator>', 'creator', '$text']      => ['author']
            WARNING: $self returns the original Tag object
    

valid value args: ['@attr', '$text', '$innerXML', '$outerXML', '$self']

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors

https://github.com/ClericPy/uniparser
```
## RegexParser (re)

```
RegexParser. Parse the input object with standard regex, features from `re`.
    Since regex input object always should be string, _RECURSION_LIST will be True.

        :param input_object: input object, could be str.
        :type input_object: [str]
        :param param: standard regex
        :type param: [str]
        :param value: operation for each item of result
        :type value: [str]

            @some string: using re.sub

            $0: re.finditer and return list of the whole matched string

            $1: re.finditer, $1 means return list of group 1

            '': null str, means using re.findall method

            -: return re.split(param, input_object)

        :return: list of str
        :rtype: List[Union[str]]

        examples:

            ['a a b b c c', 'a|c', '@b']     => 'b b b b b b'
            ['a a b b c c', 'a', '']         => ['a', 'a']
            ['a a b b c c', 'a (a b)', '$0'] => ['a a b']
            ['a a b b c c', 'a (a b)', '$1'] => ['a b']
            ['a a b b c c', 'b', '-']        => ['a a ', ' ', ' c c']
    

https://docs.microsoft.com/en-us/dotnet/standard/base-types/regular-expression-language-quick-reference

https://regex101.com/
```
## JSONPathParser (jsonpath)

```
JSONPath parser, requires `jsonpath-rw-ext` lib.
    Since json input object may be dict / list, _RECURSION_LIST will be False.

        :param input_object: input object, could be str, list, dict.
        :type input_object: [str, list, dict]
        :param param: JSON path
        :type param: [str]
        :param value: attribute of find result, default to '' as '$value'
        :type value: [str, None]
        :return: list of str
        :rtype: List[Union[str]]

        examples:

            [{'a': {'b': {'c': 1}}}, '$..c', ''] => [1]
    

https://github.com/sileht/python-jsonpath-rw-ext

https://jsonpath.com/
```
## ObjectPathParser (objectpath)

```
ObjectPath parser, requires `objectpath` lib.
    Since json input object may be dict / list, _RECURSION_LIST will be False.

        :param input_object: input object, could be str, list, dict.
        :type input_object: [str, list, dict]
        :param param: ObjectPath
        :type param: [str]
        :param value: not to use
        :type value: [Any]

        examples:

            [{'a': {'b': {'c': 1}}}, '$..c', ''] => [1]
    

http://github.com/adriank/ObjectPath

http://objectpath.org/
```
## JMESPathParser (jmespath)

```
JMESPath parser, requires `jmespath` lib.
    Since json input object may be dict / list, _RECURSION_LIST will be False.

        :param input_object: input object, could be str, list, dict.
        :type input_object: [str, list, dict]
        :param param: JMESPath
        :type param: [str]
        :param value: not to use
        :type value: [Any]

        examples:

            [{'a': {'b': {'c': 1}}}, 'a.b.c', ''] => 1
    

https://github.com/jmespath/jmespath.py

http://jmespath.org/
```
## PythonParser (python)

```
PythonParser. Some frequently-used utils.
    Since python input object may be any type, _RECURSION_LIST will be False.

        :param input_object: input object, any object.
        :type input_object: [object]
        param & value:

            1.  param: getitem, alias to get
                value: could be [0] as index, [1:3] as slice, ['key'] for dict
            2.  param: split
                value: return input_object.split(value or None)
            3.  param: join
                value: return value.join(input_object)
            4.  param: chain
                value: nonsense `value` variable. return list(itertools.chain(*input_object))
            5.  param: const
                value: return value if value else input_object
            6.  param: template
                value: Template.safe_substitute(input_object=input_object, **input_object if isinstance(input_object, dict))
            7.  param: index
                value: value can be number string / key.
            8.  param: sort
                value: value can be asc (default) / desc.
            9.  param: strip
                value: chars. return str(input_object).strip(value)
            10. param: base64_encode, base64_decode
                from string to string.
            11. param: a number for index, will try to get input_object.__getitem__(int(param))
                value: default string
                similar to `param=default` if param is 0
        examples:

            [[1, 2, 3], 'getitem', '[-1]']              => 3
            [[1, 2, 3], 'getitem', '[:2]']              => [1, 2]
            ['abc', 'getitem', '[::-1]']                => 'cba'
            [{'a': '1'}, 'getitem', 'a']                => '1'
            [{'a': '1'}, 'get', 'a']                    => '1'
            ['a b\tc \n \td', 'split', '']              => ['a', 'b', 'c', 'd']
            [['a', 'b', 'c', 'd'], 'join', '']          => 'abcd'
            [['aaa', ['b'], ['c', 'd']], 'chain', '']   => ['a', 'a', 'a', 'b', 'c', 'd']
            ['python', 'template', '1 $input_object 2'] => '1 python 2'
            [[1], 'index', '0']                         => 1
            ['python', 'index', '-1']                   => 'n'
            [{'a': '1'}, 'index', 'a']                  => '1'
            ['adcb', 'sort', '']                        => ['a', 'b', 'c', 'd']
            [[1, 3, 2, 4], 'sort', 'desc']              => [4, 3, 2, 1]
            ['aabbcc', 'strip', 'a']                    => 'bbcc'
            ['aabbcc', 'strip', 'ac']                   => 'bb'
            [' \t a ', 'strip', '']                     => 'a'
            ['a', 'default', 'b']                       => 'a'
            ['', 'default', 'b']                        => 'b'
            [' ', 'default', 'b']                       => 'b'
            ['a', 'base64_encode', '']                  => 'YQ=='
            ['YQ==', 'base64_decode', '']               => 'a'
            ['a', '0', 'b']                             => 'a'
            ['', '0', 'b']                              => 'b'
            [None, '0', 'b']                            => 'b'
            [{0: 'a'}, '0', 'a']                        => 'a'


valid param args: ['getitem', 'get', 'split', 'join', 'chain', 'const', 'template', 'index', 'sort', 'strip', 'default', 'base64_encode', 'base64_decode']

https://docs.python.org/3/

https://github.com/ClericPy/uniparser
```
## UDFParser (udf)

```
UDFParser. Python source code snippets. globals will contain `input_object` and `context` variables.
    Since python input object may be any type, _RECURSION_LIST will be False.

        param & value:
            param: the python source code to be exec(param), either have the function named `parse`, or will return eval(param)
            value: will be renamed to `context`, which can be used in parser function. `value` often be set as the dict of request & response.
        examples:

            ['a b c d', 'input_object[::-1]', '']                                                       => 'd c b a'
            ['a b c d', 'context["key"]', {'key': 'value'}]                                             => 'value'
            ['a b c d', 'md5(input_object)', '']                                                        => '713f592bd537f7725d491a03e837d64a'
            ['["string"]', 'json_loads(input_object)', '']                                              => ['string']
            ['["string"]', 'json_loads(obj)', '']                                                       => ['string']
            [['string'], 'json_dumps(input_object)', '']                                                => '["string"]'
            ['a b c d', 'parse = lambda input_object: input_object', '']                                => 'a b c d'
            ['a b c d', 'def parse(input_object): context["key"]="new";return context', {'key': 'old'}] => {'key': 'new'}
    

_GLOBALS_ARGS: ['md5', 'json_loads', 'json_dumps', 're', 'encode_as_base64', 'decode_as_base64']

https://docs.python.org/3/

https://github.com/ClericPy/uniparser
```
## LoaderParser (loader)

```
LoaderParser. Loads string with json / yaml / toml standard format.
    And also b16decode, b16encode, b32decode, b32encode, b64decode, b64encode, b85decode, b85encode.
    Since input object should be string, _RECURSION_LIST will be True.

        :param input_object: str match format of json / yaml / toml
        :type input_object: [str]
        :param param: loader name, such as: json, yaml, toml
        :type param: [str]
        :param value: some kwargs, input as json string
        :type value: [str]

        examples:

            ['{"a": "b"}', 'json', '']   => {'a': 'b'}
            ['a = "a"', 'toml', '']      => {'a': 'a'}
            ['animal: pets', 'yaml', ''] => {'animal': 'pets'}
            ['a', 'b64encode', '']       => 'YQ=='
            ['YQ==', 'b64decode', '']    => 'a'

    

valid param args: ['json', 'toml', 'yaml', 'yaml_safe_load', 'yaml_full_load', 'b16decode', 'b16encode', 'b32decode', 'b32encode', 'b64decode', 'b64encode', 'b85decode', 'b85encode']

https://github.com/ClericPy/uniparser

https://github.com/ClericPy/uniparser
```
## TimeParser (time)

```
TimeParser. Parse different format of time. Sometimes time string need a preprocessing with regex.
    Since input object can not be list, _RECURSION_LIST will be True.
        To change time zone:
            uniparser.time.LOCAL_TIME_ZONE = +8

        :param input_object: str
        :type input_object: [str]
        :param param: encode / decode. encode: time string => timestamp; decode: timestamp => time string
        :type param: [str]
        :param value: standard strftime/strptime format
        :type value: [str]

        examples:

            ['2020-02-03 20:29:45', 'encode', '']                  => 1580732985.0
            ['1580732985.1873155', 'decode', '']                   => '2020-02-03 20:29:45'
            ['2020-02-03T20:29:45', 'encode', '%Y-%m-%dT%H:%M:%S'] => 1580732985.0
            ['1580732985.1873155', 'decode', '%b %d %Y %H:%M:%S']  => 'Feb 03 2020 20:29:45'

    WARNING: time.struct_time do not have timezone info, so %z is always the local timezone
    

_OS_LOCAL_TIME_ZONE: 8
LOCAL_TIME_ZONE: 8

https://github.com/ClericPy/uniparser

https://github.com/ClericPy/uniparser
```
