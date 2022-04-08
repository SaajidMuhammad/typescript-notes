# Global state

## Creating and using global state

```
import React from  'react';
import  { createState, useState }  from  '@hookstate/core';

const globalState =  createState(null);

globalState.set("Saajid")

export  const  ExampleComponent  =  ()  =>  {
  const state =  useState(globalState);
  return  (
	<>
   My Name is {state.get()}

	</>)  
}
```

## Creating and using local state

```
import React from  'react';
import { useState }  from  '@hookstate/core';

export  const  ExampleComponent  =  ()  =>  {
  const state =  useState(0);

  return  <>
  <b>Counter value:  {state.get()}  </b>
  <button  onClick={()  => state.set(p  => p +  1)}>Increment</button>
  </>
}
```

## Accessing and mutating nested state

```
import React from  'react';
import  { useState, State }  from  '@hookstate/core';

interface  Marks  { subject: string; marks?: number }

export  const  MarksComponent  =  ()  =>  {
  const marksState: State<Marks[]>  =  useState([{ subject:  'English' }]  as Task[]);

  return  <>

	  {marksState.map((markState: Marks<Marks>, taskIndex)  =>
		  <MarksEditor  key={taskIndex}  markState={markState}  />
	  )}

	  <button  onClick={()  => marksState.merge([{ subject:  'New Subject'  }])}>Add Subject</button>

  </>
}

const MarksEditor = (props:  { markState: State<Marks>  }) =>  {
  const markState = props.markState;
  return  (
	  <p>
		  <input
			  value={markState.subject.get()}
			  onChange={e  => markState.subject.set(e.target.value)}
		   />
	  </p>)
}

```

## Advanced mutations for an object state

### Setting new state value

```
const state =  useState({ a:  1, b:  2  })

// New state value can be also a function, which returns new value and accepts the previous one:
state.set({ a:  2, b:  3  })
state.set(p  =>  ({ a: p.a +  1, b: p.b -  1  }))
	
// New state value can be also a function, which returns new value and accepts the previous one:
state.set(p  =>  ({ a: p.a +  1, b: p.b -  1  }))

```

### Getting names of existing properties

```

const state =  useState({ a:  1, b:  2  })

const keys = state.keys // will be ['a', 'b'] for the above example

```


### Updating existing property

```

const state =  useState({ a:  1, b:  2  })

state.a.set(p  => p +  1)  // increments value of property a

// or
state['a'].set(p  => p +  1)

// or
state.merge(p  =>  ({ a: p.a +  1  }))

```

#### Avoid the following:

```

state.set(p  =>  ({  ...p, a: p.a +  1  }))

state['a'].set(state.a.value +  1)  // increments value of property a

```

### Adding a new property

```
const state = useState<{ a:  number, b?:  number  }>({ a:  1  })  // notice b property is optional

state.b.set(2)
// or
state['b'].set(2)
// or
state.merge({ b:  2  })

```

### Deleting an existing property

```
const state = useState<{ a:  number, b?:  number  }>({ a:  1, b:  2  })  // notice b property is optional

import  { none }  from  '@hookstate/core'

state.b.set(none)
// or
state['b'].set(none)
// or
state.merge({ b: none })
```
