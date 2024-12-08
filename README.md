# User Dataclass Tutorial

In this tutorial, we will explore how to define a `User` class using Python's `dataclasses` module and Pydantic library. The `dataclasses` module provides a decorator and functions for automatically adding generated special methods to user-defined classes. Pydantic, on the other hand, is used for data validation and settings management using Python type annotations.

## Prerequisites

Before you start this tutorial, make sure you have Python 3.7 or higher installed on your system. You will also need to install the Pydantic library, which can be done using pip:

```bash
pip install pydantic
```

## Tutorial Content

### Importing Required Modules

We begin by importing the necessary modules:

```python
from dataclasses import dataclass, field 
from typing import List, Optional
from pydantic import Field, TypeAdapter
```

### Defining the User Class

Next, we define the `User` class using the `@dataclass` decorator:

```python
@dataclass
class User:
    id: int 
    name: str = 'John Doe'
    age: Optional[int] = field(
        default=None,
        metadata=dict(title='The age of the user', description='do not lie!', ge=18)
    )
    height: Optional[int] = Field(None, title='The height in cm', ge=50, le=300)
    friends: List[int] = field(default_factory=lambda: [0])
```

#### Fields Explanation

- `id`: An integer field representing the user's ID.
- `name`: A string field with a default value of 'John Doe'.
- `age`: An optional integer field with metadata for validation (age must be at least 18).
- `height`: An optional integer field with validation for height range (50 cm to 300 cm).
- `friends`: A list of integers with a default value of `[0]`.

### Using the User Class

Once the `User` class is defined, you can create instances of it and access its fields:

```python
user = User(id=1, name='Alice', age=25, height=170, friends=[2, 3, 4])
print(user)
```

This will output:

```
User(id=1, name='Alice', age=25, height=170, friends=[2, 3, 4])
```

## Conclusion

In this tutorial, we learned how to define a dataclass in Python and enhance it with Pydantic for data validation. The `User` class demonstrates how to use default values, metadata, and validation rules to ensure that the data is consistent and meets the specified criteria.

You can now use this pattern to define other dataclasses in your projects and leverage the power of Pydantic for data validation and settings management.

## Additional Resources

For more information on `dataclasses` and Pydantic, please refer to the following resources:

- [Data Classes](https://docs.python.org/3/library/dataclasses.html)
- [Pydantic Documentation](https://pydantic-docs.helpmanual.io/)

Happy coding!