# Manage global state with context objects
Use context objects (by dependency injection) to encapsulate the state and pass them around as needed. Below is a sample code:

```C++
class Context {
public:
    void setValue(int val) { value = val; }
    int getValue() const { return value; }

private:
    int value = 0;
};

void someFunction(Context& ctx) {
    ctx.setValue(42);
}

int main() {
    Context ctx;
    someFunction(ctx);
    std::cout << "Value: " << ctx.getValue() << std::endl;
    return 0;
}
```

Note that this implementation can be combined with the single pattern to ensure that there is only one instance.

#todo make sample code for "manage global state with singleton pattern".