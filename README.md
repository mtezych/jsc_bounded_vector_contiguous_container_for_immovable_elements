
## [`jsc::bounded_vector<>`](https://code.fmsolvr.fz-juelich.de/ATML-CAP/jsc-cxx/src/branch/main/include/jsc/bounded_vector.hpp) contiguous container for immovable elements

### Abstract

For the last 30 years `std::vector` has been the default choice for a sequence container in C++.  
Specialized containers, such as `std::inplace_vector` or `llvm::SmallVector`, have been introduced  
in order to fill the gaps that `std::vector` does not cover. Unfortunately no contiguous container,  
with capacity defined at run-time, supports immovable elements, such as synchronization primitives - until now.  
The `jsc::bounded_vector` has been designed with this exact use case in mind.  

During the talk I will take a listener on a journey, explaining why yet another vector is needed  
and how its design came to be. I will show that while designing and implementing `jsc::bounded_vector`,  
it turned out that its interface is not only flexible enough to cover the vast majority of `std::vector` use cases,  
but also so consistent and ergonomic that using it in generic code is seamless and intuitive.  
Moreover, `jsc::bounded_vector` has been designed from the ground up to integrate really well  
with the C++ ranges library, thus, in my view, it is just a clean and modern re-implementation of `std::vector`  
that is intentionally more suitable for real-time systems and GPU programming,  
due to guaranteed / predictable memory usage and full / explicit control over memory allocations.  

In the presentation I will deep dive into the guts of the C++ standard library and  
show its limitations and shortcomings that prevent `std::vector` from supporting guaranteed copy-elision,  
and therefore immovable elements. During this segment I will not only highlight the issues,  
but also show programming techniques and generic components, some of which are Rust inspired,  
that fix or improve the status-quo, by providing stronger compile-time guarantees,  
less run-time overhead, better consistency and more control.  
These techniques and components can be reused independently in other C++ projects,  
thus they are not just building blocks of `jsc::bounded_vector`, but have much wider applicability.  
All of the discussed code is fully open source and freely available today.  