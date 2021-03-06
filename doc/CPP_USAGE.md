Usage of C++ within RNP
============================

This is a provisional document reflecting the recent conversion from C
to C++. It should be revisited as experience with using C++ within RNP
codebase increases.

Encouraged Features
====================

These are features which seem broadly useful, their downsides are minimal
and well understood.

 - STL types std::vector, std::string, std::unique_ptr, std::map

 - RAII techniques (destructors, smart pointers) to minimize use of
   goto to handle cleanup.

 - Value types, that is to say types which simply encapsulate some
   data without

 - std::function or virtual functions to replace function pointers.

 - Prefer virtual functions only on "interface" classes (with no data),
   and derive only one level of classes from this interface class.

 - Anonymous namespaces are an alternative to `static` functions.

Questionable Features
=======================

These are features that may be useful in certain situations, but should
be used carefully.

 - Exceptions. Which convenient they do have a non-zero cost in runtime
   and binary size.

Forbidden Features
======================

These are C++ features that simply should be avoided, at least until a
very clear use case for them has been identified and no other approach
suffices.

 - RTTI. This has a significant runtime cost and usually there are
   better alternatives.

 - Multiple inheritence. This leads to many confusing and problematic
   scenarious.

 - Template metaprogramming. If you have a problem, and you think
   template metaprogramming will solve it, now you have two problems,
   and one of them is incomprehensible.
