When you create a piece of React state, you assign a new memory address to it.

If you want to change this state, you have to call `setState` and provide the new object that updates the properties you want.

When you do that, you create a brand new object that lives on a different part of the memory.

Because React state is **immutable**, when you change it, you're not changing the value of the memory address. You are creating a whole new object that lives somewhere else. Eventually, the old object will be deleted by the JS garbage collector.

If you have multiple state variables, only the ones that changed will have a new memory address.