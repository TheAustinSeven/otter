#Otter (the easy Collaboration engine)
This program is intended to make real-time collaboration easy. This is done with Operation Transformation, a technique through which operations are "transformed" according to the ones before them. This means that if we have two operations `delete(2)` and `insert(3,'a')` they will be transformed according to what is run before them. In this case when `insert` is run first, `delete` is unchanged, but if `delete` is run first, then `insert` must be changed so that it inserts one earlier.

Otter is being built in C so that it runs, as the professionals put it, "super-duper" fast. This will allow the wrappers to simply make a call to the optimized C, and everything can run nice and fast. 

The plan is to use Redis to power the memory portion of this. The reason for this is because Redis is robust, fast, and most importantly, fault tolerant. 

##API
Currently the api is still being planned, but I have a pretty good idea of what I want it to look like. I am thinking that it should look something like this:

- int create_document(string document_contents)
- void insert(int document_id, int insertion_point, string insertion_contents, int parent_id, int parent_machine_id)
- void delete(int document_id, int start_of_range, int end_of_range, int parent_id, int parent_machine_id)
- string get_document_string(int document_id)
- string get_operations_buffer(int document_id, int start_id)
- void update_document(string updated_document_contents)
- string close_document(int document_id)

As of right now, it will be the developer's responsibility to pull the operations buffer for each client, but that will likely be added functionality in later versions.

##Contributing
Right now this is a personal project, and I want to bring this to version 1 by myself, but if you are interested in building a language wrapper for Otter, start an issue on this repository and we can start to discuss how this should be done.

## License
Otter is released under the [MIT License](http://www.opensource.org/licenses/MIT).
