<!-- TITLE: Ipython -->
<!-- SUBTITLE: A quick summary of Ipython -->

# Ways to dump Objects

```text
dir(objectname)
vars(objectname)
help(objectname)

```

# Way to drop to debugging prompt
```
import pdb
pdb.set_trace()
```

one hint said 1/0 should do it.  I saw warnings, but it didn't kick to prompt.  Perhaps a way somewhere.

# Save an object for later analysis
>>> import pickle
>>> pickle.dumps(seen)
b'\x80\x03}q\x00X\x03\x00\x00\x00fooq\x01X\x03\x00\x00\x00barq\x02s.'
>>> pickle.loads(_)
