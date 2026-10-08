### Functions in Terraform

1. Validation Functions
2. Lookup Fucntion
3. Date and time Function
4. File Function
5. String Function
6. Numeric Functions
7. Collection Functions
8. Type Conversion

```
join(separator, list)
join(",", ["foo", "bar", "baz"])

upper(string)
lower(string)
trim(string, separator) #Trimming spaces
replace(string, substring1, substring2)
substr(string, 0, 3)
max
min
abs
sum
length([1,2,3,4])
concat([1,2],[3,4])
merge(tags, common_tags) #merge two maps
split(separator, list)
lookup(var.instance_sizes, var.environment, "t2.micro") #Instance_sizes is a map variable
validation functions in variable --> regex, can, contains, startsWith, endsWith
toset
timestamp()
formatdate("yyyyMMdd", local.current_timestamp)
fileexists()
jsondecode(file("./config.json"))
```