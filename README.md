# boolean-vector-pattern-matching
C++ Snippet for matching multiple occurrences of the pattern in the source boolean vector

```
#include <iostream>
#include <vector>
#include <algorithm>
#include <iterator>

int main(int argc, char* argv[])
{

    std::vector<bool> haystack{0,0,0,0,1,1,1,1,1,0,1,0,1,0,0,0,0,1,1,1,1,1,1,1,1,1,1,1};
    std::vector<bool> needle{1,1,1,1};

    std::vector<bool>::iterator res;
    int dist = std::distance(needle.begin(), needle.end());
    res = std::search(haystack.begin(), haystack.end(), needle.begin(), needle.end());
    
    if (res != haystack.end()) {
        std::cout << "needle is present at index " << (res - haystack.begin()) << std::endl;
    } else {
        std::cout << "needle is not present in haystack" << std::endl;
        return -1;
    }
    
    while(res < haystack.end())
    {
      std::advance(res, dist);
      res = std::search(res, haystack.end(), needle.begin(), needle.end());
      
      if(res >= haystack.end()) 
        break;
      
      std::cout << "needle is present at index " << (res - haystack.begin()) << std::endl;
    }
    
    return 0;
}
```

### Output:

```
needle is present at index 4
needle is present at index 17
needle is present at index 21
```
