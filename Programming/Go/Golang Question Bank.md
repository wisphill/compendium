---
flashcard_uid: 9732085c
cssclasses: true-recall-cards
parents:
  - "[[Golang]]"
---
#flashcards


**What is the entry point of an executable Go program?<span class="tr-accent-blue tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">The `main` function in `package main`.</span>
<!-- true-recall: {"v":1,"id":"770c5b97-c550-41c9-919c-e1b73a8fb121","schedules":[{"updatedAt":1793523989260,"due":"2026-11-01T09:06:29.260Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989260}],"bases":{"dagoj9f7":{"front":"48f3a2eb5f22d149413190e25719c24e068c15209cbd22b154bd737f4fc56269","back":"78ffe735d4e8eb33aa55fa769ec39e6b4f0b17e2217e42cf8e39c5f821e2ed66","reversed":false}}} -->

**What is the difference between `var` and `:=`?<span class="tr-accent-mint tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">`var` can be used at package or function scope; `:=` declares and initializes variables only inside functions.</span>
<!-- true-recall: {"v":1,"id":"b921b115-39d8-47bb-8bd6-fe15e6e2fe8a","schedules":[{"updatedAt":1793523989263,"due":"2026-11-01T09:06:29.263Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989263}],"bases":{"dagoj9f7":{"front":"a429e094603419e210f514103cfbe05b8458b49b52df9d038f0dff36cf938caf","back":"cd061bc5c1a47dffa5158d80719ae52f07cf3060bb50c9ef3c354d28ff263052","reversed":false}}} -->

**What does `defer` do?<span class="tr-accent-coral tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It schedules a function call to run when the surrounding function returns.</span>
<!-- true-recall: {"v":1,"id":"d1b8d66e-92f1-4ab8-9642-ea0be4a8c797","schedules":[{"updatedAt":1793523989265,"due":"2026-11-01T09:06:29.265Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989265}],"bases":{"dagoj9f7":{"front":"470d9dd2d4c925a52fe73603350dbb2f3ce2fe9993bc913bb7b1620c49252204","back":"c7f6641807fa51f76031029bb4c7b86b308c5475373fd36ee927aaa180adc9eb","reversed":false}}} -->

**How does Go normally handle expected errors?<span class="tr-accent-purple tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Functions return an `error` value, which callers check explicitly.</span>
<!-- true-recall: {"v":1,"id":"afadbc0c-afa1-4ce4-8b68-dea7d2e39a28","schedules":[{"updatedAt":1793523989266,"due":"2026-11-01T09:06:29.266Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989266}],"bases":{"dagoj9f7":{"front":"a02e9014f99bc93869ef452fe892e1158c3bb847bad5bfbce2c42ff3841b662b","back":"6d32c6b0e6bb617dd1053f8f240f39414d25a8ccbd153b1b80410889601993b5","reversed":false}}} -->

## Types and collections

**What is the difference between an array and a slice in Go?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">An array has a fixed length that is part of its type; a slice is a flexible descriptor over an underlying array.</span>
<!-- true-recall: {"v":1,"id":"f4074afd-b992-43d3-8aec-7099f55a0ed9","schedules":[{"updatedAt":1793523989268,"due":"2026-11-01T09:06:29.268Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989268}],"bases":{"dagoj9f7":{"front":"3ef6fce7b9e4d05b900c204fdf80169f4c421ec816e846c488071daea85947e6","back":"d60a13b5751847ec2eda0f6b47f2c2ce84f6ec3604e9f8e1cffda5e170c3f605","reversed":false}}} -->

**How do you test whether a key is present in a map?<span class="tr-accent-teal tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Use the comma-ok form: `value, ok := m[key]`.</span>
<!-- true-recall: {"v":1,"id":"7bf50c01-8cd6-4ce3-b970-b8f0a58c4a4f","schedules":[{"updatedAt":1793523989270,"due":"2026-11-01T09:06:29.270Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989270}],"bases":{"dagoj9f7":{"front":"bb0e27414b19fbe4ef6bc0d511c688694c2608bb6bfd3fc14f2c07e227dababd","back":"db0060b66c3084b79cbee300432c7b0e26692b47a23b973da1bb9610aaaf7cc5","reversed":false}}} -->

**What is a Go interface?<span class="tr-accent-coral tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A set of method signatures that a type satisfies implicitly by implementing those methods.</span>
<!-- true-recall: {"v":1,"id":"4a6378cf-7c9d-465c-9e67-8938c62fb23e","schedules":[{"updatedAt":1793547705722,"due":"2026-11-11T15:41:45.698Z","stability":8.2956,"difficulty":1,"reps":1,"lapses":0,"state":2,"lastReview":"2026-11-01T15:41:45.698Z","scheduledDays":10,"learningStep":0,"suspended":false,"createdAt":1793523989271}],"bases":{"dagoj9f7":{"front":"1f27b2cb7393d7f4dff54ffaf8d7abc1386eefe158e03a01b5f93e242fd617c8","back":"08ae68cc32688114965e8809ad0d5f1477652b64df690c3eb4520b5c5554ad51","reversed":false}}} -->

**When should you use a pointer receiver for a method?<span class="tr-accent-blue tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">When the method must modify the receiver or copying the receiver would be expensive.</span>
<!-- true-recall: {"v":1,"id":"9b01b10f-139b-4e4d-9cd5-e543a985ff54","schedules":[{"updatedAt":1793523989273,"due":"2026-11-01T09:06:29.273Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989273}],"bases":{"dagoj9f7":{"front":"3a7fb211eb6dc2278788f537f268e3e4fef639a1e00e89b3642f0320bd019a17","back":"28ef7cfde9d74aa1646adf917912abc3863cf4ba6795e6e2756d93e67f657e01","reversed":false}}} -->

## Concurrency

**What is a goroutine?<span class="tr-accent-purple tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A lightweight concurrent function started with the `go` keyword.</span>
<!-- true-recall: {"v":1,"id":"267e9375-6647-49ab-b4ad-bf122f04e3b9","schedules":[{"updatedAt":1793523989275,"due":"2026-11-01T09:06:29.275Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989275}],"bases":{"dagoj9f7":{"front":"2f2d428e5ed20b49d8881591273466885c6992ccc65887dcc4c5550bcc55aa38","back":"2b4d5a08366c71691a88ee4ea165096fe1ee7aa9fa8b673f373489b5ed867110","reversed":false}}} -->

**What is a channel?<span class="tr-accent-mint tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">A typed mechanism for communicating values between goroutines.</span>
<!-- true-recall: {"v":1,"id":"9c88d3c1-cb52-4596-a044-257fdb17580a","schedules":[{"updatedAt":1793523989276,"due":"2026-11-01T09:06:29.276Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989276}],"bases":{"dagoj9f7":{"front":"7feebb07a33590a577dbef954a632b1c6db2b153121ba7acf7a99817ca0b5c62","back":"0272158d2afd48012edefe33b1fe2d7619c208d51ef0990b5d6ed833e86c7b2a","reversed":false}}} -->

**How do buffered and unbuffered channels differ?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">`An unbuffered send` waits for a receiver; a buffered channel can hold values up to its capacity before a send blocks. One has queue while other ones do not have it.</span>
<!-- true-recall: {"v":1,"id":"bb8862ee-79fc-4b91-b88d-2a66cadf47ee","schedules":[{"updatedAt":1793523989278,"due":"2026-11-01T09:06:29.278Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989278}],"bases":{"dagoj9f7":{"front":"3eb1bdb58c20a4855650a1a8c4f3c0badd31a3fcefeb3517fa5e405de42b97b1","back":"8c3fd1cb474c76181bf8697f10f824bfdc2f67a301bd58d88e9244398a1f033a","reversed":false}}} -->

**What is `select` used for?<span class="tr-accent-teal tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It waits until one of several channel operations can proceed.</span>
<!-- true-recall: {"v":1,"id":"202f644b-4cc0-41c3-9896-4ee37e5946c4","schedules":[{"updatedAt":1793523989279,"due":"2026-11-01T09:06:29.279Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989279}],"bases":{"dagoj9f7":{"front":"fa4f1fe39a8ca0eb76f3f559d149330224ad3e7cf1226771d7b9adfa7180a528","back":"2b39a9883bad30d1f7ecf87ae0f1a1a1805c3ead388d3a533f4a8bd8551f6c18","reversed":false}}} -->

**How can you detect data races while testing Go code?<span class="tr-accent-blue tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Run `go test -race ./...`.</span>
<!-- true-recall: {"v":1,"id":"66ffffd9-561c-43ba-ac76-84a51160aeaa","schedules":[{"updatedAt":1793523989280,"due":"2026-11-01T09:06:29.280Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989280}],"bases":{"dagoj9f7":{"front":"8c92b1715bcfb42c1a37d4534b7c5e45bbeba11e93e0b9661dbe45bb7236c21f","back":"035a0a190132146077a9d7e10a26d3d411e81877abe0d0a4fb5efa60c73ac621","reversed":false}}} -->

## Tooling and practices
**What is `context.Context` used for?<span class="tr-accent-coral tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">To propagate cancellation, deadlines, and request-scoped values across API boundaries.</span>
<!-- true-recall: {"v":1,"id":"909ee428-55df-4f91-9040-155e036a92cd","schedules":[{"updatedAt":1793523989281,"due":"2026-11-01T09:06:29.281Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989281}],"bases":{"dagoj9f7":{"front":"06539d4c7d0939a6b11a84a7984daa6c0b20b192b1afc5935fa672c6e9aa0270","back":"4a314aa2408a39b43e6ddf9aa2f3ec1fd0c9d85b3a946cafae63344cd718e1d7","reversed":false}}} -->

**How do you run all tests in a Go module?<span class="tr-accent-mint tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">Run `go test ./...`.</span>
<!-- true-recall: {"v":1,"id":"347336a7-760e-432b-80f7-a3dd9b6a975a","schedules":[{"updatedAt":1793523989282,"due":"2026-11-01T09:06:29.282Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989282}],"bases":{"dagoj9f7":{"front":"fd93cc6d8c4f0e3d2de0af49e5867d7f81b0bed1d12b28ee09418a8e50d38e76","back":"e381948efe482fbd56f01f9f6333b0cb20e268c7a6ee3faf788f174efc8ec421","reversed":false}}} -->

**What does `go mod tidy` do?<span class="tr-accent-purple tr-tail-right"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It adds missing module requirements and removes module dependencies that are no longer needed.</span>
<!-- true-recall: {"v":1,"id":"baedae18-89cf-4288-8c8c-58057b8d6866","schedules":[{"updatedAt":1793523989285,"due":"2026-11-01T09:06:29.285Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989285}],"bases":{"dagoj9f7":{"front":"6cfff992561cc003390a90066355bf0efd7a055f3e09ec9ffee1676278d95b7a","back":"35e02f8e8d0537914a490681ec0a4dc4effb9ea40e48790e7ae4dfc0803ca42b","reversed":false}}} -->

**Why should Go source files be formatted with `gofmt`?<span class="tr-accent-amber tr-tail-left"></span>**
<span class="tr-card-separator">??</span>
<span class="tr-card-answer">It applies Go's standard formatting rules, keeping code consistent and easy to review.</span>
<!-- true-recall: {"v":1,"id":"6e198a85-29c9-4747-a7e4-d58608bfa2c1","schedules":[{"updatedAt":1793523989286,"due":"2026-11-01T09:06:29.286Z","stability":0,"difficulty":0,"reps":0,"lapses":0,"state":0,"lastReview":null,"scheduledDays":0,"learningStep":0,"suspended":false,"createdAt":1793523989286}],"bases":{"dagoj9f7":{"front":"00df81ed492776cbba05d9fb35dcd9f5acd08672578d4721c7a8fa2c80e3ea59","back":"da6cef590fca0f0004aab77a533d8e5a8bb6f380495453d5bbb2c96a1712cc13","reversed":false}}} -->
