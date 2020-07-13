# How to call lookup plugin from action plugin

```python
from ansible.plugins.lookup.template import LookupModule as TemplateLookup


class ActionModule(ActionBase):

    def run(self, tmp=None, task_vars=None):
        result = super(ActionModule, self).run(tmp, task_vars)
        kwargs = {}
        lookup = TemplateLookup(self._loader, self._templar, **kwargs)
        lookup = lookup.run(['file.txt'], task_vars, **kwargs)
        result['lookup'] = lookup
        return result

```
