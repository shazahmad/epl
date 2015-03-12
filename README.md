Engineering Programming Language Project Discription
====================================================
Instructor: Prof. Craig Chase

Engineering Programming Language (EPL) is a graduate software design and implementation class that emphasizes engineering level insight into the mechanics of contemporary programming languages. EPL makes extensive use of the C++ language (C++11), in part because C++ is sufficiently low level that the mechanics by which object-oriented programming are implemented become readily visible to C++ programmers. Topics covered in EPL change annually, but often include, Template Meta Programming, Object Oriented Design, Design for Performance, Memory Management and Garbage Collection.

Project1. Vector Container Basics and Extensions
------------------------------------------------
###Part1 - Basics
This project is to implement the container vector. A vector is a data structure that provides O(1) random access (via an operator[]), and amortized constant append (via push_back). Our vector differs from the standard library vector in three minor ways. We are not required to implement all of the C++ standard functions, our operator[] performs bounds checking, and we have to implement a “push_front” and “pop_front”.

Method List:

    - vector(void) – creates an array with some minimum capacity (8 is fine) and length equal to zero. Must not use T::T(void). In fact, as long as Vector::Vector(int) is not called, we shall never use T::T(void)
    - explicit Vector(uint64_t n) – create an array with capacity and length exactly equal to n. Initialize the n objects using T::T(void). As a special case, if n is equal to zero, you can duplicate the behavior of vector(void).
    - copy and move constructors for vector<T> arguments
    - copy and move assignment operators for vector<T> arguments
    - destructor
    - uint64_t size(void) const – return the number of constructed objects in the vector
    - T& operator[](uint64_t k) – if k is out of bounds (equal to or larger than length), then we will throw std::out_of_range(“subscript out of range”). If k is in bounds, then we return a reference to the element at position k
    - const T& operator[](uint64_t k) const – same as above, except for constants.
    - void push_back(const T&) – add a new value to the end of the array, using amortized doubling if the array has to be resized. Copy construct the argument.
    - void push_back(T&&) – same as above, but move construct the argument.
    - void push_front(const T&) and void push_front(T&&) -- similar to push_back, but add the element to the front of the Vector
    - void pop_back(void) and (B) void pop_front(void) – if the array is empty, throw a std::out_of_range exception (with any reasonable string error message you want). Otherwise, destroy the object at the end (or beginning) of the array and update the length. This action will not reallocate storage, even if the vector becomes empty. It is possible that a vector can have available capacity at both the front and back simultaneously. 

Note :
We implement amortized doubling whenever we increase the allocated space of your vector.
If a call to pop_back succeeds (does not throw an exception) and is followed immediately by a call to push_back, then we will not perform any memory allocations. More generally, if two or more consecutive calls to pop_back succeed and are followed by an equal number of calls to push_back, then no allocations are performed. Similarly if one or more successive calls to pop_front succeed and are followed immediately by an equal number of push_front calls, then no memory allocations are performed.
