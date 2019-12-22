# fileloghelper

A simple helper for logging content to files (and displaying it)

## Methods

- set_context(context): specifies context which will be added to all outputs (file & terminal) in front
- success(text, display=True): writes text to file and optionally with green indication in console (if display==True)
- debug(text, display=True): writes text to file and optionally with blue indication in console (if display==True)
- warning(text, display=True): writes text to file and optionally with yellow indication in console (if display==True)
- error(text, display=True): writes text to file and optionally with red indication in console (if display==True)
- plain(text, display=False, extra_long): write and optionally display text to file. extra_long specifies time format (12:34:56; 12:34:56:123456)
- save(): save file under default/at declaration specified filename

### Example

```python
from fileloghelper import Logger

logger = Logger(filename='log.txt', context='MyLogger')

logger.debug('Hello World!', display=False)
logger.success('Successfull!', display=True)

logger.save()
```
