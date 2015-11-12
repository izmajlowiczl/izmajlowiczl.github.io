If (param != null) ...
=====================

It is just a check, better safe than sorry, you said? One more check for null reference makes not much difference but multiplied by hundreds, spreaded on many levels of abstraction, pushed inside business logic, definitely can make a difference.

In this article, I would like to highlight problem which I noticed, many of us repeat each day. Null checks for almost every value possibly we can find. I will try to convince you to put more attention on values we return, design by contract and testing. All related to NULLs.

During some talks to fellows developers I noticed that this topic can be quite controversial and hope that people with different point of view will contribute by commenting below this post.

### So why do we overuse null-checks?
I believe that most of the cases comes from being not familiar with code we use. We try to create safety net by blindly checking all params passed to methods in order to “just be sure” it will work.

Luck of experience is second reason. Not knowing alternative ways to structure code, missing knowledge in design patterns, language syntax or just good practices can lead to defensive programming.

Third, and in my eyes the worst reason is adding null-checks after getting NullPointerExceptions. Having not better idea how to solve NPEs in the first place and adding just another check as a quick fix. 

### OK, but why is it so bad?
Despite wasting finger power to type extra lines of code, the bigger problem for me is introducing waste in the code. For many developers it makes not a big deal but for those who care about readability, clean code and testing it makes a big difference.

Another problem is introducing duplication in code. Let’s take as an example standard J2EE call for data. Having few layers like, DB -> Repository -> Service -> Client, some coders can check for null in Repository, Service and Client which sounds for me pretty much like duplication.

This few extra lines of code increase complexity of code. Adding null-check indicates that we should act on this check by showing error to client, throwing extra exception or passing this value higher in call stack or whatever suits context better. Additionally we need to increase test coverage for code which can be not related to business logic.

### You says to remove all null-checks?
There is few places where null is just valid construct or other solutions makes simply no sense. The good thing to remember is to always design by contract, document your code and prove in tests that null value is what you planned to do.

### When to check for a null?
You should definitely check for them in code you own and you took confident decision that it makes sense. The less obvious places, but still worth checking is code which doesn’t belong to us. All 3rd party libraries, framework methods and other which sources are not available are good candidates to check. 

Why I believe that we should check there? Simply, because code can change from version to version, documentations get out of sync with code and laziness of coders.

### When to avoid check for null?
All places which we control should be null-free (unless it really makes sense). We should be confident about our code and use it wisely. Write, read documentation and keep it in sync with code changes to be always sure what another check is not needed.

Checking in many layers of abstraction is definitely bad idea. Trying to handle situation when object returned by code not controlled by us as soon as possible should make client code cleaner and more concentrated on business logic instead of error handling.

Most of those situations can be fixed by refactoring code or introducing null object design pattern. Not returning null from our methods can significantly improve our situation. In many cases we could return empty collection instead of null. Good practices and some design patterns can save us from necessity of null-checks.

### Conclusion
To sumarise, try to avoid checking for null references in code which you own and double think whether methods in libraries you use need these checks as well. Handle these cases as soon as possible in order to not mess client code which should be concentrated on business logic instead of error handling. Design your contracts and return null only when any good practices, design patterns or default values does not make sense. Always test your assumptions and stay decoupled from frameworks and 3rd party libraries.
