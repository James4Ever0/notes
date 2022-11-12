---
tags: [fault tolerance, hack, ignore error, ignore exception, python]
title: 'Python Bytecode, Time Travel Debugging, Resurrection, Ante-Mortem Debugging, Interactive Debugging, Resume after Exception, Python ignore all exceptions and continue execute next line in given section of code, edit and continue'
created: '2022-07-11T14:57:00.000Z'
modified: '2022-11-12T20:04:58.819Z'
---

# Python Bytecode, Time Travel Debugging, Resurrection, Ante-Mortem Debugging, Interactive Debugging, Resume after Exception, Python ignore all exceptions and continue execute next line in given section of code

[why i hate exceptions](http://xahlee.info/comp/why_i_hate_exceptions.html)

## lisp-style resumption error-handling semantics

[python for lisp programmers](https://norvig.com/python-lisp.html)

[practical common lisp](https://gigamonkeys.com/book/)

[arithmatic infix](http://www.cs.cmu.edu/afs/cs/project/ai-repository/ai/lang/lisp/code/syntax/infix/infix.cl)

[common lisp debugging](https://lisp-journey.gitlab.io/blog/debugging-in-common-lisp/#inspect-and-describe)

[common lisp related libraries](https://awesome-cl.com/#apl)

[slime](https://slime.common-lisp.dev/)

[portacle](https://portacle.github.io/)

[talk on reddit](https://www.reddit.com/r/lisp/comments/d0vv00/is_the_common_lisp_style_of_interactive_debugging/)

## ruby

[pry-rescue](https://github.com/conradirwin/pry-rescue) may not resume execution?

## java

[eclipse hot code swap fix](https://www.appsloveworld.com/eclipse/100/12/eclipse-edit-the-source-and-continue-debugging)

[hot code replace in vscode for java](https://code.visualstudio.com/docs/java/java-debugging)

## python

[bytecode hack, pyhotswap](https://github.com/albertz/PythonHotswap/blob/master/FuncModify.py)

[python lisp-style exception as condition handling](https://python-cl-conditions.readthedocs.io/en/latest/)

dump different level of reloading call history

reload code blocks which are syntatically different, if black formatter fails after dedent then there shall be error

decide to reload extra parts of functions in the next run if selected

load newly added functions, remove old functions, execute added lines, reload entire module and update namespace depending on condition

check other programming language whether it jas similar capabilities

[visit this thread of ruby in archive.org](https://newbedev.org/guide/ruby-continue-in-same-loop-iteration-after-an-exception)

[wallabyjs](https://wallabyjs.com/purchase/#select-wallaby)

either bytecode or modify the source code

## bookmarks

```html
https://docs.python.org/3/library/code.html
https://docs.python.org/3/library/cmd.html
https://docs.python.org/3/library/threading.html#threading.settrace
https://mail.python.org/archives/list/python-dev@python.org/thread/OGPO6KWHQGO47KOJKNEWNZS3LLMVXBEV/
https://github.com/TomOnTime/timetravelpdb
https://github.com/nfd/on_error_resume_next/blob/master/basic.py
https://github.com/search?p=5&q=BEFORE_ASYNC_WITH&type=Code
https://github.com/Martmists-GH/pyasm/blob/a306f23cbed13505687eb0ca86f010e5fe3101b5/asm/ops/py35.py
https://github.com/Martmists-GH/pyasm
https://github.com/kr1surb4n/copypaster_filedecks/blob/3f2ca44c4f984652585a1e7f1e589966e8867da6/filedecks_archive/python/library/dis/Python%20Bytecode%20Instructions/opcodeBEFOREASYNCWIT
https://github.com/kholia/dedrop/blob/60da43889be89950cadbbb6b54489eb1841c70da/src/dedrop-ng/opcode_mapper.py
https://github.com/brettlangdon/gython
https://github.com/Exitialium/Github-Drive/blob/5284358a163c4ea25c63f4157d41af5f638950a2/deap/include/python3.9/opcode.h
https://github.com/ajalt/fuckitpy
https://code.lardcave.net/2020/12/29/1/
https://github.com/asrp/python_terp/blob/master/test/buggy_ex.py
https://github.com/HugoDelval/reversibleInterpreter
https://github.com/topics/reversible-programming-language
https://github.com/jndean/railway/wiki/Variables,-Data-and-Scope
https://cn.bing.com/search?q=python+run+bytecode&qs=UT&pq=python+run+byteco&sc=1-17&cvid=79F89EEA4A564540BF79A8DBB63284CE&FORM=QBRE&sp=1
https://opensource.com/article/18/4/introduction-python-bytecode
http://www.aosabook.org/en/500L/a-python-interpreter-written-in-python.html
https://github.com/nedbat/byterun
https://unpyc.sourceforge.net/Opcodes.html
https://docs.python.org/3/library/codeop.html
https://docs.python.org/3/library/dis.html
https://docs.python.org/3/library/dis.html
https://docs.python.org/3/library/codeop.html
https://blog.quarkslab.com/building-an-obfuscated-python-interpreter-we-need-more-opcodes.html
https://github.com/fietensen/PyOpcodeAsm
https://pypi.org/project/BytecodeAssembler/
http://probablyprogramming.com/2008/04/18/ppya-python-assembler
https://pypi.org/project/BytecodeAssembler/#description
http://peak.telecommunity.com/DevCenter/BytecodeAssembler
https://github.com/pib/papaya
https://www.programcreek.com/python/?CodeExample=get+opcode
https://unpyc.sourceforge.net/Opcodes.html
https://www.synopsys.com/blogs/software-security/understanding-python-bytecode/
https://github.com/neuroo/equip
https://tenthousandmeters.com/blog/python-behind-the-scenes-4-how-python-bytecode-is-executed/
https://tenthousandmeters.com/blog/python-behind-the-scenes-5-how-variables-are-implemented-in-cpython/
https://discuss.python.org/t/exec-with-return-keyword/19916/25
https://cn.bing.com/search?q=interactive%20debugging%20python&qs=n&form=QBRE&=%25eManage%20Your%20Search%20History%25E&sp=-1&pq=interactive%20debugging%20&sc=3-22&sk=&cvid=30D653A233984DD685DE7CE79AD46318&ghsh=0&ghacc=0&ghpl=
https://www.digitalocean.com/community/tutorials/how-to-debug-python-with-an-interactive-console
https://nedbatchelder.com/blog/200509/interactive_debugging_in_python.html
https://derpops.bike/python/computers/kubernetes/2017/10/26/interactive-debugging-python-kubernetes.html
https://bytes.com/topic/python/answers/46053-resume-after-exception
https://pytrace.com/
https://github.com/gleb-sevruk/pycrunch-trace/issues
```

contextlib usage detail, to make customized "with" statements:

```python
from contextlib import AbstractContextManager

class suppress2(AbstractContextManager):
    """Context manager to suppress specified exceptions

    After the exception is suppressed, execution proceeds with the next
    statement following the with statement.

         with suppress(FileNotFoundError):
             os.remove(somefile)
         # Execution still resumes here if the file was already removed
    """

    def __init__(self, *exceptions):
        self._exceptions = exceptions

    def __enter__(self):
        print(dir(self))
        pass

    def __exit__(self, exctype, excinst, exctb):
        # Unlike isinstance and issubclass, CPython exception handling
        # currently only looks at the concrete type hierarchy (ignoring
        # the instance and subclass checking hooks). While Guido considers
        # that a bug rather than a feature, it's a fairly hard one to fix
        # due to various internal implementation details. suppress provides
        # the simpler issubclass based semantics, rather than trying to
        # exactly reproduce the limitations of the CPython interpreter.
        #
        # See http://bugs.python.org/issue12029 for more details
        print("EXCTYPE", exctype)
        print("EXCINST", excinst)
        print("EXCTB",exctb) # exception
        print(dir(exctb))
        breakpoint()
        return exctype is not None and issubclass(exctype, self._exceptions)
```

python grammar sugar: brackets
https://pypi.org/project/brackets/
does that work in eval()?

use contextlib.suppress to replace try...except: pass
might investigate source code of the suppress object.

https://opensource.com/article/18/5/how-retrieve-source-code-python-functions

to execute code grouped by lowest level of indentation, we can def those lines of code and pass the code by dill.source.getsource(functionName) and eval within given global/local variables.

my solution is down here, with concrete examples.

hereby we recommend to insert a conditional return statement to ensure we will exit this buggy code at the best time. maybe we could put it into a dictionary somehow, tuples within string or something.

```python
import dill
from contextlib import suppress
import traceback

def skipException(func, debug_flag=False, breakpoint_flag=False):

    def space_counter(line):
        counter = 0
        for x in line:
            if x == " ": counter+=1
            else: break
        return counter

    def remove_extra_return(code):
        while True:
            if "\n\n" in code:
                code = code.replace("\n\n","\n")
            else: break
        return code
    
    def isEmptyLine(line):
        emptyChars = ["\n","\t","\r"," "]
        length = len(line)
        emptyCounts=0
        for char in line:
            if char in emptyChars: emptyCounts += 1
        return emptyCounts == length
    
    def getCodeBlocks(lines):
        mBlocks=[]
        current_block = lines[0]
        lines = lines+[""]
        keywords = [" ", "def", "async def", "with", "class", "@"]
        for line in lines[1:]:
            if sum([line.startswith(keyword) for keyword in keywords]):
                current_block+="\n"
                current_block+=line
            else:
                mBlocks.append(current_block)
                current_block = line
        return mBlocks
    
    def getExtendedLines(splited_code):
        splited_code = [x.rstrip() for x in splited_code]
        splited_code = "\n".join(splited_code).replace("\\\n","")
        splited_code = remove_extra_return(splited_code)
        splited_code = splited_code.split("\n")
        return splited_code
    

    def new_func(*args, **kwargs):
        func_name = func.__name__
        func_code = dill.source.getsource(func)
        if debug_flag:
            print("########## FUNCTION CODE #########")
            print(func_code) # do not use chained decorator since doing so will definitely fail everything?
            print("########## FUNCTION CODE #########")
            print("########## FUNCTION #########")
        # print(func_code)
        func_code = remove_extra_return(func_code)
        splited_code = func_code.split("\n")
        splited_code = getExtendedLines(splited_code)
        # index 0: decorator
        # index 1: function name
        # no recursion support. may work inside another undecorated function.
        try:
            assert splited_code[0].strip().startswith("@skipException")
        except:
            raise Exception("Do not nesting the use of @skipException decorator")
        function_definition = splited_code[1]
        function_args=function_definition[:-1].replace("def {}".format(func_name),"")
        if debug_flag:
            print("FUNCTION ARGS:", function_args)
        kwdefaults = func.__defaults__
        pass_kwargs = {}

        if "=" in function_args:
            assert kwdefaults!=None
            arg_remains = function_args.split("=")[0]
            kwarg_remains = function_args.replace(arg_remains,"")
            kwarg_extra_names =[content.split(",")[-1].strip() for index, content in enumerate(kwarg_remains.split("=")) if index%2 ==1]
            mfunctionArgsPrimitive = arg_remains.replace("(","").split(",")
            kwarg_names = [mfunctionArgsPrimitive[-1].strip()]+kwarg_extra_names
            mfunctionArgs = mfunctionArgsPrimitive[:-1]
            if debug_flag:
                print("PASSED KEYWORD ARGS:", kwargs)
                print("KWARG NAMES:", kwarg_names)
            for key, value in zip(kwarg_names, kwdefaults):
                pass_kwargs.update({key: value})
            for key in kwargs.keys():
                assert key in kwarg_names
                pass_kwargs[key] = kwargs[key]
        else:
            assert kwdefaults == None
            mfunctionArgs = function_args.replace("(","").replace(")","").split(",")
        mfunctionArgs = [x.strip() for x in mfunctionArgs]
        mfunctionArgs = [x for x in mfunctionArgs if not isEmptyLine(x)]
        if debug_flag:
            print("POSITIONAL ARGS:",mfunctionArgs)
        assert len(args) == len(mfunctionArgs)

        for key, value in zip(mfunctionArgs, args):
            exec("{} = {}".format(key, value))
        if kwdefaults is not None:
            for key, value in pass_kwargs.items():
                exec("{} = {}".format(key, value))
        actualCode = splited_code[2:]
        actualCode = [x for x in actualCode if not isEmptyLine(x)]
        minIndent = min([space_counter(line) for line in actualCode])
        # split the code into different sections.
        if debug_flag:
            print(minIndent)
        newLines = [line[minIndent:] for line in actualCode]
        codeBlocks = getCodeBlocks(newLines)
        for block in codeBlocks:
            if debug_flag:
                print("##########CODEBLOCK##########")
                print(block)
                print("##########CODEBLOCK##########")
            if not debug_flag:
                with suppress(Exception):
                    exec(block)
            else:
                try:
                    exec(block)
                except:
                    traceback.print_exc()
                    if breakpoint_flag: breakpoint()
        if debug_flag:
            print("########## FUNCTION #########")

    return new_func

def skipExceptionVerbose(func): return skipException(func, debug_flag=True)
def skipExceptionBreakpoint(func): return skipException(func, breakpoint_flag=True)
def skipExceptionDebug(func): return skipException(func, breakpoint_flag=True, debug_flag=True)

@skipException
def someOtherShit():
    amd=[1,2,3]
    amd[4]
    print("shit happens")

def anotherShit():
    @skipException
    def mySuperFunction(d,e,f):
        someOtherShit()
        print("YOU WIN")
        a = [1,2,3]
        a[3] # will not continue execute the code down there
        print("YOU WIN")
        a[4]
        print("INSIDE FUNCTION",d,e,f)
        print("YOU WIN")
    mySuperFunction(1,2,3)
    # print(dir(mySuperFunction))

anotherShit()

# breakpoint()

```
