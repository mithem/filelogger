# fileloghelper

A simple helper for logging content to files (and displaying it)

## Installation

```bash
pip3 install fileloghelper
```

## Methods

### set_context(context)

Specifies context which will be added to all outputs (file & terminal) in front

|parameter|description|
|:---:|---|
|context: str | string to be added to output of other functions|

### set_verbose(verbose)

Sets verbose mode for whole logger. If true, a info whether the text is success/debug/warning/error information will be added to the file

|parameter|description|
|:---:|---|
|verbose: bool | value to set for verbose mode |

### save()

Saves the file under default/at declaration specified filename

### clear()

Clear the log. **Note**: You have to save again to make changes to the actual file

### success(text, display=True)

Writes log to file. If verbose mode active, '[SUCCESS]' will be written in addition.

|parameter|description|
|:---:|---|
|display: bool| print text on console|

### debug(text, display=True)

Writes log to file. If verbose mode active, '[DEBUG]' will be written in addition.

|parameter|description|
|:---:|---|
|display: bool| print text on console|

### warning(text, display=True, extra_context="")

Writes log to file. If verbose mode active, [{extra_context}] will be written in addition. extra_context can be used to give extra information about the warning.

|parameter|description|
|:---:|---|
|display: bool| print text on console|

### error(text, display=True, extra_context="")

Writes log to file. If verbose mode active, [{extra_context}] will be written in addition. extra_context can be used to give extra information about the error.

|parameter|description|
|:---:|---|
|display: bool| print text on console|

### plain(text, display=False, extra_long=False, very_plain=False)

Writes log without any colors to file. If display==True, the text will be displayed. If extra_long==True, milliseconds will be added to the timestamp. If very_plain==True, the timestamp will be omitted.

### show_warning(warning: Warning, display=True)

Extracts class from warning and uses it to invoke warning() with extra_context

### show_error(error: Exception, display=True)

Extracts class from error and uses it to invoke error() with extra_context

### handle_exception(exception: Exception)

Automatically categorizes exception to invoke show_warning() or show_error()

### header(sys_stat=False, date=False, description="", display=0)

Use plain() to output certain information:

|parameter|description|
|:---:|---|
|sys_stat|write system information to the log|
|date|write date information to the log|
|description|write the specified description to the log|
|display|also display certain information in the console (see table below)|

**Modes for display:**

|mode number|information printed|
|:---:|---|
|0 (standard) | none
1 | description only
2 | date only
3 | system information only
4 | description & date
5 | description & system information
6 | date & system information
7 | all above

## Example

```python
from fileloghelper import Logger

logger = Logger(filename='log.txt', context='MyLogger')

logger.header(sys_stat=True, date=True, description='A short description', display=7)
logger.debug('Hello World!', display=False)
logger.success('Successfull!', display=True)
logger.handle_exception(NotImplementedError("off to work!"))

logger.save()
```
