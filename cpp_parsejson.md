# How to parse JSON files in C++
Popular libraries for working with JSON in C++ include nlohmann/json, RapidJSON, jsoncpp, and so many more.

>[!important]
>Check out the [benchmarks for native JSON libraries](https://github.com/miloyip/nativejson-benchmark).
>![[performance_Corei7-4980HQ@2.80GHz_mac64_clang7.0_1._Parse_Time_(ms).png|300]]

For this guide, [nlohmann/json](https://github.com/nlohmann/json) library is used to read and parse a JSON file.

## Install the library
- There are two options for installing the library - using CMAKE to compile the library, or using a header-only library.
- For simplicity sake, the header-only library is used.
	- On the library github page, go to `single_include/nlohmann` and download `json.hpp`.
	- Put the header file in the project (e.g. in the `include` folder).
- Include the header, like so:

```C++
#include <nlohmann/json.hpp>

using json = nlohmann::json; // for convenience
```

## Prepare a JSON file
- Example JSON file (e.g. `data.json`) with content:

```json
{
    "name": "John Doe",
    "age": 30,
    "is_student": false,
    "skills": ["C++", "Python", "JavaScript"],
    "address": {
        "street": "123 Main St",
        "city": "Somewhere",
        "zipcode": 12345
    }
}
```

## Read a JSON file
- Just like with any other files, a JSON file is read using `std::ifstream` from the `<fstream>` library:

```C++
#include <iostream>
#include <fstream>
#include <nlohmann/json.hpp>

using json = nlohmann::json;

int main() {
    // Open the JSON file
    std::ifstream file("data.json");
    if (!file.is_open()) {
        std::cerr << "Error: Could not open the file!" << std::endl;
        return 1;
    }

	return 0;
}
```

- The content of `file` is then streamed into a `json` object:

```C++
// Parse the JSON file
json jsonData;
file >> jsonData;  // Read data into a json object
```

### json::parse(file)
- The library also provides a function to read from a JSON file:

```C++
// Open the JSON file
std::ifstream file("data.json");
json jsonData = json::parse(file);
```

## Accessing values from a JSON object
- The values of the JSON object can be accessed, like so:

```C++
// Access values from the JSON
std::string name = jsonData["name"];
int age = jsonData["age"];
bool isStudent = jsonData["is_student"];
std::vector<std::string> skills = jsonData["skills"];
std::string street = jsonData["address"]["street"];
std::string city = jsonData["address"]["city"];
int zipcode = jsonData["address"]["zipcode"];
```

- The values of the JSON object can then be displayed:

```C++
// Display the parsed data
std::cout << "Name: " << name << std::endl;
std::cout << "Age: " << age << std::endl;
std::cout << "Is Student: " << (isStudent ? "Yes" : "No") << std::endl;
std::cout << "Skills: ";
for (const auto& skill : skills) {
	std::cout << skill << " ";
}
std::cout << std::endl;
std::cout << "Address: " << street << ", " << city << ", " << zipcode << std::endl;
```

- Once compiled, the result of the code above should print out as shown below:

```console
Name: John Doe
Age: 30
Is Student: No
Skills: C++ Python JavaScript 
Address: 123 Main St, Somewhere, 12345
```



## Create a JSON object
- A JSON object can be created from a scratch without reading from a file:

```C++
json newJson;
newJson["name"] = "Jane Doe";
newJson["age"] = 25;
newJson["skills"] = {"C++", "Java", "HTML"};
newJson["address"] = {{"street", "456 Elm St"}, {"city", "Anywhere"}, {"zipcode", 67890}};
```

## Write a JSON file
- A JSON object (with data) can be written to a file:

```C++
std::ofstream outFile("output.json");

if (!outFile.is_open()) {
	std::cerr << "Error opening file!" << std::endl;
	return 1;
}

outFile << newJson.dump(4);  // Pretty print with 4 spaces

outFile.close();
```

## Serialize a JSON object to a string
- A JSON object can be serialized to a `std::string` object:

```C++
std::string jsonString = newJson.dump();  // Convert JSON to string
std::cout << jsonString << std::endl;
```

## Error handling
- When a value that does not exist in the JSON object, it throws an `std::out_of_range` error:

```C++
try {
    auto value = jsonData.at("nonexistent_key");  // Throws if the key doesn't exist
} catch (std::out_of_range& e) {
    std::cerr << "Key not found: " << e.what() << std::endl;
}
```

## Create a JSON object from literals
- There are three different ways to create a JSON object from literals:

```C++
// Using (raw) string literals and json::parse
json ex1 = json::parse(R"(
  {
    "pi": 3.141,
    "happy": true
  }
)");

// Using user-defined (raw) string literals
using namespace nlohmann::literals;
json ex2 = R"(
  {
    "pi": 3.141,
    "happy": true
  }
)"_json;

// Using initializer lists
json ex3 = {
  {"happy", true},
  {"pi", 3.141},
};
```

