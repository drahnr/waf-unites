## waf-unites

[![Join the chat at https://gitter.im/drahnr/waf-unites](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/drahnr/waf-unites?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

A simple yet powerfull unit test suite


Runs tests on each build unless `--notests` is passed. The return value of the waf build process will be set to nonzero if one or more tests fail. It also has a permissive mode to allow tests to fail.

### Usage

Just copy the `unites.py` file to your project directory (where the desired waf file is, other wise you have to adjust the `tooldir=` path)

```python
def options(opt):
    opt.load('unites', tooldir='.')
    ...

def configure(cfg):
    cfg.load('unites', tooldir='.')
    ...


def build(bld):
    # build your regular binary here
    #...
    
    # build any number of tests, just make sure it has the `unites` feature
	atest = bld.program(
		features = ['c', 'unites'],
		target = 'multi-client-test',
		source = ['test/multi-client.c'],
		includes = ['src'],
		...
		)

```
