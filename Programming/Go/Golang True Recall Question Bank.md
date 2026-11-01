---
flashcard_uid: 9732085c
---
#flashcards
**What is the entry point of an executable Go program?**
??
The `main` function in `package main`.
<!-- true-recall: {"v":1,"id":"770c5b97-c550-41c9-919c-e1b73a8fb121","schedules":[{"updatedAt":1793523989260,"due":"2026-11-01T09:06:29.260Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989260}],"bases":{"dagoj9f7":{"front":"a5f0387fbf06fdfd331f8620b9e33d2ed42d09c6a26da6bdf7330212234468f7","back":"78ffe735d4e8eb33aa55fa769ec39e6b4f0b17e2217e42cf8e39c5f821e2ed66","reversed":false}}} -->

**What is the difference between `var` and `:=`?**
??
`var` can be used at package or function scope; `:=` declares and initializes variables only inside functions.
<!-- true-recall: {"v":1,"id":"b921b115-39d8-47bb-8bd6-fe15e6e2fe8a","schedules":[{"updatedAt":1793523989263,"due":"2026-11-01T09:06:29.263Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989263}],"bases":{"dagoj9f7":{"front":"275d59254d677d2f6a425cfdbbe7ba1edd592e925eb4f3a741fd90cd3a88726a","back":"cd061bc5c1a47dffa5158d80719ae52f07cf3060bb50c9ef3c354d28ff263052","reversed":false}}} -->

**What does `defer` do?**
??
It schedules a function call to run when the surrounding function returns.
<!-- true-recall: {"v":1,"id":"d1b8d66e-92f1-4ab8-9642-ea0be4a8c797","schedules":[{"updatedAt":1793523989265,"due":"2026-11-01T09:06:29.265Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989265}],"bases":{"dagoj9f7":{"front":"3e14250b878287cd6e2e2178abc9bb30b5989fd6c4aaf10d805bff19d71f5e16","back":"c7f6641807fa51f76031029bb4c7b86b308c5475373fd36ee927aaa180adc9eb","reversed":false}}} -->

**How does Go normally handle expected errors?**
??
Functions return an `error` value, which callers check explicitly.
<!-- true-recall: {"v":1,"id":"afadbc0c-afa1-4ce4-8b68-dea7d2e39a28","schedules":[{"updatedAt":1793523989266,"due":"2026-11-01T09:06:29.266Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989266}],"bases":{"dagoj9f7":{"front":"5f046e1e926b1d919c0bb363e8a65ab01b4c6c9ecd17409d432b24042a90f3a5","back":"6d32c6b0e6bb617dd1053f8f240f39414d25a8ccbd153b1b80410889601993b5","reversed":false}}} -->

## Types and collections

**What is the difference between an array and a slice in Go?**
??
An array has a fixed length that is part of its type; a slice is a flexible descriptor over an underlying array.
<!-- true-recall: {"v":1,"id":"f4074afd-b992-43d3-8aec-7099f55a0ed9","schedules":[{"updatedAt":1793523989268,"due":"2026-11-01T09:06:29.268Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989268}],"bases":{"dagoj9f7":{"front":"8632746dbdba942451a436609ae8c15fd961f127d8c37849e86c5a0f1ad5bfdb","back":"d60a13b5751847ec2eda0f6b47f2c2ce84f6ec3604e9f8e1cffda5e170c3f605","reversed":false}}} -->

**How do you test whether a key is present in a map?**
??
Use the comma-ok form: `value, ok := m[key]`.
<!-- true-recall: {"v":1,"id":"7bf50c01-8cd6-4ce3-b970-b8f0a58c4a4f","schedules":[{"updatedAt":1793523989270,"due":"2026-11-01T09:06:29.270Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989270}],"bases":{"dagoj9f7":{"front":"60ba131a19971c98267080890935e2b9b292e2a303c4277acdf760ffea8bdc55","back":"db0060b66c3084b79cbee300432c7b0e26692b47a23b973da1bb9610aaaf7cc5","reversed":false}}} -->

**What is a Go interface?**
??
A set of method signatures that a type satisfies implicitly by implementing those methods.
<!-- true-recall: {"v":1,"id":"4a6378cf-7c9d-465c-9e67-8938c62fb23e","schedules":[{"updatedAt":1793523989271,"due":"2026-11-01T09:06:29.271Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989271}],"bases":{"dagoj9f7":{"front":"023216de47ea7ead242979d1e6e5dba6b7ade549cb985c105889016f038c2203","back":"08ae68cc32688114965e8809ad0d5f1477652b64df690c3eb4520b5c5554ad51","reversed":false}}} -->

**When should you use a pointer receiver for a method?**
??
When the method must modify the receiver or copying the receiver would be expensive.
<!-- true-recall: {"v":1,"id":"9b01b10f-139b-4e4d-9cd5-e543a985ff54","schedules":[{"updatedAt":1793523989273,"due":"2026-11-01T09:06:29.273Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989273}],"bases":{"dagoj9f7":{"front":"7c9f14b1bb6a5b5e8ba083e869184ec5db6010c026e2d0f302f81b082edaaa0a","back":"28ef7cfde9d74aa1646adf917912abc3863cf4ba6795e6e2756d93e67f657e01","reversed":false}}} -->

## Concurrency

**What is a goroutine?**
??
A lightweight concurrent function started with the `go` keyword.
<!-- true-recall: {"v":1,"id":"267e9375-6647-49ab-b4ad-bf122f04e3b9","schedules":[{"updatedAt":1793523989275,"due":"2026-11-01T09:06:29.275Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989275}],"bases":{"dagoj9f7":{"front":"aa5739ca8acf6e63213ab06c09f27b35e0a9bb2fd509ab2b770caf82299395fc","back":"2b4d5a08366c71691a88ee4ea165096fe1ee7aa9fa8b673f373489b5ed867110","reversed":false}}} -->

**What is a channel?**
??
A typed mechanism for communicating values between goroutines.
<!-- true-recall: {"v":1,"id":"9c88d3c1-cb52-4596-a044-257fdb17580a","schedules":[{"updatedAt":1793523989276,"due":"2026-11-01T09:06:29.276Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989276}],"bases":{"dagoj9f7":{"front":"4ec29a87fb84b8b82d44df4d6e834b53bfd8a5b6efea5f6528db0c833d14feb0","back":"0272158d2afd48012edefe33b1fe2d7619c208d51ef0990b5d6ed833e86c7b2a","reversed":false}}} -->

**How do buffered and unbuffered channels differ?**
??
`An unbuffered send` waits for a receiver; a buffered channel can hold values up to its capacity before a send blocks. One has queue while other ones do not have it.
<!-- true-recall: {"v":1,"id":"bb8862ee-79fc-4b91-b88d-2a66cadf47ee","schedules":[{"updatedAt":1793523989278,"due":"2026-11-01T09:06:29.278Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989278}],"bases":{"dagoj9f7":{"front":"871978ff75482c1fff96110116ca15d43cb1bc81dae48c40ab0a0fe43c1a897e","back":"8c3fd1cb474c76181bf8697f10f824bfdc2f67a301bd58d88e9244398a1f033a","reversed":false}}} -->

**What is `select` used for?**
??
It waits until one of several channel operations can proceed.
<!-- true-recall: {"v":1,"id":"202f644b-4cc0-41c3-9896-4ee37e5946c4","schedules":[{"updatedAt":1793523989279,"due":"2026-11-01T09:06:29.279Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989279}],"bases":{"dagoj9f7":{"front":"4e3b007692448859bcae4127e5d82e4fea2c839e0a8db554af451c89cdbd12ff","back":"2b39a9883bad30d1f7ecf87ae0f1a1a1805c3ead388d3a533f4a8bd8551f6c18","reversed":false}}} -->

**How can you detect data races while testing Go code?**
??
Run `go test -race ./...`.
<!-- true-recall: {"v":1,"id":"66ffffd9-561c-43ba-ac76-84a51160aeaa","schedules":[{"updatedAt":1793523989280,"due":"2026-11-01T09:06:29.280Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989280}],"bases":{"dagoj9f7":{"front":"b4e8fc933e02db3406f0ca2833f426359e03f41f4236d4e4129ccd818198f693","back":"035a0a190132146077a9d7e10a26d3d411e81877abe0d0a4fb5efa60c73ac621","reversed":false}}} -->

## Tooling and practices
**What is `context.Context` used for?**
??
To propagate cancellation, deadlines, and request-scoped values across API boundaries.
<!-- true-recall: {"v":1,"id":"909ee428-55df-4f91-9040-155e036a92cd","schedules":[{"updatedAt":1793523989281,"due":"2026-11-01T09:06:29.281Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989281}],"bases":{"dagoj9f7":{"front":"1010b2424c3fcca5d2dbd6d95bfaa0e02d5681fc6892af5484d1fedcb044e359","back":"4a314aa2408a39b43e6ddf9aa2f3ec1fd0c9d85b3a946cafae63344cd718e1d7","reversed":false}}} -->

**How do you run all tests in a Go module?**
??
Run `go test ./...`.
<!-- true-recall: {"v":1,"id":"347336a7-760e-432b-80f7-a3dd9b6a975a","schedules":[{"updatedAt":1793523989282,"due":"2026-11-01T09:06:29.282Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989282}],"bases":{"dagoj9f7":{"front":"c68168fad318504d8918cfc37aa0a8c52507aaf976c0c22fd8b208f986ac2147","back":"e381948efe482fbd56f01f9f6333b0cb20e268c7a6ee3faf788f174efc8ec421","reversed":false}}} -->

**What does `go mod tidy` do?**
??
It adds missing module requirements and removes module dependencies that are no longer needed.
<!-- true-recall: {"v":1,"id":"baedae18-89cf-4288-8c8c-58057b8d6866","schedules":[{"updatedAt":1793523989285,"due":"2026-11-01T09:06:29.285Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989285}],"bases":{"dagoj9f7":{"front":"7066be8434dd584d84145e09afb2c018b205edf4a0fe859460638c62e4332e71","back":"35e02f8e8d0537914a490681ec0a4dc4effb9ea40e48790e7ae4dfc0803ca42b","reversed":false}}} -->

**Why should Go source files be formatted with `gofmt`?**
??
It applies Go's standard formatting rules, keeping code consistent and easy to review.
<!-- true-recall: {"v":1,"id":"6e198a85-29c9-4747-a7e4-d58608bfa2c1","schedules":[{"updatedAt":1793523989286,"due":"2026-11-01T09:06:29.286Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989286}],"bases":{"dagoj9f7":{"front":"e69b342c32584cb6d88af61dea315c4ce220f96b419f62586352365acacc632b","back":"da6cef590fca0f0004aab77a533d8e5a8bb6f380495453d5bbb2c96a1712cc13","reversed":false}}} -->
