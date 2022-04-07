# TypeScript + React

## Basic Prop Types Examples

```
type AppProps = {
  message: string;
  count: number;
  disabled: boolean;
  
  // array of a type!
  names: string[]; 
  
  // union type
  status: "waiting" | "success";

  obj: object;
  obj2: {};
  
  // an object with any number of properties (PREFERRED)
  obj3: {
    id: string;
    title: string;
  };
  
  // array of objects! 
  objArr: {
    id: string;
    title: string;
  }[];
  
  
  dict1: {
    [key: string]: MyTypeHere;
  };
  dict2: Record<string, MyTypeHere>; // equivalent to dict1
 
  onSomething: Function;
 
  onClick: () => void;
  
  onChange: (id: number) => void;

  onChange: (event: React.ChangeEvent<HTMLInputElement>) => void;
 
  onClick(event: React.MouseEvent<HTMLButtonElement>): void;
  
  // an optional prop (VERY COMMON!)
  optional?: OptionalType;
};

```

## React Prop Type Examples

```
export declare interface AppProps {

  children1: JSX.Element; // bad, doesnt account for arrays
  
  children2: JSX.Element | JSX.Element[]; // meh, doesn't accept strings
  
  children3: React.ReactChildren; // despite the name, not at all an appropriate type; it is a utility
  
  children4: React.ReactChild[]; // better, accepts array children
  
  children: React.ReactNode; // best, accepts everything (see edge case below)
  
  functionChildren: (name: string) => React.ReactNode; // recommended function as a child render prop type
  
  style?: React.CSSProperties; // to pass through style props
  
  onChange?: React.FormEventHandler<HTMLInputElement>; // form events! the generic parameter is the type of event.target

  props: Props & React.ComponentPropsWithoutRef<"button">; // to impersonate all the props of a button element and explicitly not forwarding its ref
  
  props2: Props & React.ComponentPropsWithRef<MyButtonWithForwardRef>; // to impersonate all the props of MyButtonForwardedRef and explicitly forwarding its ref
}
```

<hr>


## Types or Interfaces?

-   always use  `interface`  for public API's definition when authoring a library or 3rd party ambient type definitions, as this allows a consumer to extend them via  _declaration merging_  if some definitions are missing.
    
-   consider using  `type`  for your React Component Props and State, for consistency and because it is more constrained.

Ref : https://medium.com/@martin_hotell/interface-vs-type-alias-in-typescript-2-7-2a8f1777af4c


# Function Components

```
// Declaring type of props - see "Typing Component Props" for more examples

type AppProps = {
  message: string;
}; 

/* use `interface` if exporting so that consumers can extend */

// Easiest way to declare a Function Component; return type is inferred.
const App = ({ message }: AppProps) => <div>{message}</div>;

// you can choose annotate the return type so an error is raised if you accidentally return some other type
const App = ({ message }: AppProps): JSX.Element => <div>{message}</div>;

// you can also inline the type declaration; eliminates naming the prop types, but looks repetitive
const App = ({ message }: { message: string }) => <div>{message}</div>;
```
