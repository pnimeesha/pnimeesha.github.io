Before reading this post, try to answer this [question](https://discord.com/channels/1237280313927798785/1286932882232836146/1400882946059010048). I explain the answer to this question in the post.

### 1. What’s Pydantic?

Pydantic is a Python library that helps you define "data models" with types, and it automatically validates data.

Example:
```python
from pydantic import BaseModel

class Post(BaseModel):
    an_author_id: int
    a_content: str
```
Now if you do:
```python
post = Post(an_author_id=1, a_content="Hi!")
print(post.a_content)  # works fine
```

### 2. The helper function

You want to write a function like this:
```python
def parse_pydantic_model_from_json(model, data):
    json_data = json.loads(data)
    return model.model_validate(json_data)
```
But there’s a problem, If you use it like this:
```python
post = parse_pydantic_model_from_json(Post, '{"an_author_id": 1, "a_content": "Hi"}')
post.   # No autocomplete in IDE
```
Your editor doesn’t know that ```post``` is a ```Post``` object. It just thinks it’s some generic object.

### 3. Add typing
We can help Python (and the IDE) know the return type by using TypeVar and BaseModel.
```python
from typing import Type, TypeVar
from pydantic import BaseModel
import json

# T will stand for "any subclass of BaseModel"
T = TypeVar("T", bound=BaseModel)

def parse_pydantic_model_from_json(model: Type[T], data: str) -> T:
    json_data = json.loads(data)
    return model.model_validate(json_data)
```

Now when you use the function:
```python
class Post(BaseModel):
    an_author_id: int
    a_content: str

post = parse_pydantic_model_from_json(Post, '{"an_author_id": 1, "a_content": "Hi"}')
print(post.a_content)   #  autocomplete works!!
```
If you type ```post.``` in your editor, it will show suggestions:
- ```an_author_id```
- ```a_content```

*One of the reasons autocompletion engineering matters for ML platform work is that it improves productivity and developer experience, Abstraction, saftey, maitainability and many more!

where can you learn this:
- [Python to production](https://www.udemy.com/course/setting-up-the-linux-terminal-for-software-development/)
- [Mlopsclub.org](https://mlops-club.org/)
