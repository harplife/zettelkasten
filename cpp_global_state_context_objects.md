# Manage global state with context objects
Use context objects 

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