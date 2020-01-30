# 71st meeting of Ecma TC39
# High-level overview

Stage 4, ready to ship: 
Promise.allSettled [bug](https://bugzilla.mozilla.org/show_bug.cgi?id=1549176)
Two syntax changes have moved to stage 3, nullish coalescence and optional chaining
A lot of discussion around built in modules. No forward movement.
Issues with Weakref -- it cannot be tested in the current test262 setup. Discussion around how to address this.

#Editor Updates
## Test 262 report

Test262 is having problems with weak refs. It is difficult to detect problems because all of the browsers have different garbage collectors. We discussed the possibility of adding a GC hook for the tests, but it was discarded. There are also security implications. There was no clear resolution here, but it highlights an issue.

## TC53 Liaison Report

The liaison reported a change to the name
TC53: EcmaScript Modules for Embedded Systems

This highlights their support for builtin modules. They explicitly voiced their support for split namespaces, which Mozilla opposes.

# Accepted normative changes 

* Disallow internal methods returning `continue`|`break`|`return`
    * Assists formalisation and implementors
*  Disallow BigInt literals for Annex-B non-octal digits
    * Annex B was causing issues with the spec. It was not resolvable so we disable non-octal digits

# Discussions

## [Loosening idempotency requirements for HostImportModuleDynamically to enable retrying failed fetches](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-25.md#loosening-idempotency-requirements-for-hostimportmoduledynamically-to-enable-retrying-failed-fetches)
- [issue](https://github.com/tc39/proposal-dynamic-import/issues/80)
- Approved to merge the change

## [Web built-in module convention guidance from TC39](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#web-built-in-module-convention-guidance-from-tc39)
- [issue](https://github.com/heycam/webidl/issues/755)
- issue with built in modules name spacing

# Proposals Advanced Stage 4
## [Promise.allSettled](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#promiseallsettled)
- [proposal](https://github.com/tc39/proposal-promise-allSettled)
- [slides](https://docs.google.com/presentation/d/1qhYDRlsvyVUtveT2tS0mJtzG-xe9islO6-t2wMQUJso/edit)
* Moved to stage 4
* discussion around `Promise.race` being aliased to `Promise.anySettled`

# Proposals Advanced Stage 3

## [Nullish coalescing](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-23.md#nullish-coalescing)
- [proposal](https://github.com/tc39/proposal-nullish-coalescing/)
- [slides](https://1drv.ms/p/s!AltPy8G9ZDJdqSUtMZeOKLg1RcRD)
* Moved forward to stage 3
* Uses parens to address issue with conflicts between || and ?? — grammar needs to be rewritten

## [Optional Chaining for Stage 3](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-25.md#optional-chaining-for-stage-3)
- [proposal](https://github.com/tc39/proposal-optional-chaining/)
- [slides](https://onedrive.live.com/view.aspx?resid=5D3264BDC1CB4F5B!5281&ithint=file%2cpptx&authkey=!AH-MOCJRlVtK_QE)
- introduces `a?.b` `a.b?.()` `a.b?.[x]`
- Approved for stage 3

# Proposals Advanced Stage 2 or Stage 1

## [Iterator Methods Update / Stage 2](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#iterator-methods-update--stage-2)
- [proposal](https://github.com/tc39/proposal-iterator-helpers)
- [slides](https://docs.google.com/presentation/d/16Abs2Terjd2J9VJW3HZHNcp7SYdhDmpVH6DR86TxYF4/edit)
- Set of iterator methods to make it easier to work with iterators. Rather than using array.from, these methods are lazy. Example, `iter.map(func).take(5)`
- advanced to stage 2

## Explicit Resource Management
- [proposal](https://github.com/tc39/proposal-using-statement)
- [slides](https://1drv.ms/p/s!AjgWTO11Fk-TkdZAmxoB7HKzm78gCw)
- investigate syntax
- approved for stage 2

## Promise.any
- [proposal](https://github.com/tc39/proposal-promise-any/)
- [slides](https://docs.google.com/presentation/d/1WbE3squBN76_4SIHRmOQKrzglaQAVizMQZ8MqipoM4U/edit)
- The `.errors` property need not be enumerable.
- Consensus reached for Stage 2.

## [Symbol.reverse](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-23.md#symbolreverse)
* [sample code](https://gist.github.com/leobalter/092fc36adccfcc86e8e7b074817078e1)
* Moved forward to stage 1
* Allows creating a reversed iterator, a bit incomplete in its formulation

## [Dynamic Import Host Adjustment for Stage 1 or 2](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-25.md#dynamic-import-host-adjustment-for-stage-1-or-2)
- [proposal](https://github.com/mikesamuel/dynamic-import-host-adjustment)
- [slides](https://docs.google.com/presentation/d/e/2PACX-1vT42wrii3gX0dZ3ordT5QgVes0Y2WLEhsvFl4Q7svdSyve4kl3bMtqvkEauQd1uPC2JNOm3anw-1IGn/pub?start=false&loop=false&delayms=60000)
- Approved for stage 1
- Needs more discussion before stage 2

## [`Map#updateOrInsert`](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-25.md#mapupdateorinsert)
- [proposal](https://github.com/tc39/???)
- [slides](https://docs.google.com/presentation/d/1_xtrGSoN1-l2Q74eCXPHBbbrBHsVyqArWN0ebnW-pVQ/edit#slide=id.p)
- Advance to stage 1 

# Proposals with blocked advancement

## [Built-In Modules aka JavaScript Standard Library](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#built-in-modules-aka-javascript-standard-library)
- [proposal](https://github.com/tc39/proposal-javascript-standard-library)
- [slides](https://github.com/tc39/proposal-javascript-standard-library/blob/master/slides/JSL-TC39-July-2019.pdf)
- introduces a standard library
- two points of contention: 
- having a unified namespace, or a split one
- loading from scripts, synchronously
- issue two was shown to be out of order
- blocked from advancement to stage 2 on issue 1
- blocks work on temporal and other standard library work

## [Dynamic Code Brand Checks for Stage 2](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-25.md#dynamic-code-brand-checks-for-stage-2)
- [proposal](https://github.com/tc39/proposal-dynamic-code-brand-checks)
- [slides](https://docs.google.com/presentation/d/e/2PACX-1vS9iXY1nSKu2UkpqNIVmzgs5oPdgPYz8aShH4y07m7JUTR51IyOfz8KcFZ0Pf_NUnlcaf4qpgLnNOwi/pub?start=false&loop=false&delayms=60000&slide=id.p)
- no for stage 2

## [Reduce the amount of implementation-defined behavior in `Array.prototype.sort`](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#reduce-the-amount-of-implementation-defined-behavior-in-arrayprototypesort)
- [PR](https://github.com/tc39/ecma262/pull/1585)
- [slides](https://docs.google.com/presentation/d/1eFvK__9kRwHnkzZfNEL9FS3d9TJSRtxlXe3NVGmVVAU/edit)
* specifies behavior more fully based on the V8 implementation
* has consistent behavior with spidermonkey (requires no change)
* test cases are not substantial enough
* no advancement

## [`String.prototype.replaceAll`](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#stringprototypereplaceall)
- [proposal](https://github.com/tc39/proposal-string-replace-all)
- [slides](https://docs.google.com/presentation/d/194gQ-GRfb9r17Vva9nevePkFUfPck1o_pXHM25LlVKs/edit)
* investigate web compatibility for matchAll behavior, if we can make both global by default
* go with option 2 now, advancement blocked.

## [Collection Normalization update](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#collection-normalization-update)
- [slides](https://docs.google.com/presentation/d/1xxkHqtScIvdCBI4IZOpWHh7AKCJs6s5edQQu06wnZYc/edit)
- no advancement, and potentially indefinite blocker
- potentially withdrawn

## [Update on function implementation hiding](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#update-on-function-implementation-hiding)
- [proposal](https://github.com/tc39/proposal-function-implementation-hiding)
- [slides](https://docs.google.com/presentation/d/1lWH97DxTLU3_1EJA-F19uIzagZQx7PZmys7WyNXw3cY/edit)
- mask toString to hide function implementation
- further investigation needed. Seeking stage 3 at next presentation


# Proposals with unclear resolution
## [Infix Bang](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-25.md#infix-bang)
- [proposal](https://github.com/Agoric/proposal-infix-bang)
- no resolution

## [Inconsistency between Array.from and %TypedArray%.from](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-23.md#inconsistency-between-arrayfrom-and-typedarrayfrom)
* [sample code](https://gist.github.com/ljharb/896ad592accdbd783d5ec1d44e978b76)
* unclear resolution

## [Casing Conventions](https://github.com/tc39/tc39-notes/blob/master/meetings/2019-07/july-24.md#casing-conventions)
- [slides](https://docs.google.com/presentation/d/1PK01F6mkHLycz9jN8jQZrrg0Rvne4d2Sv-R-uGApYqA/edit)
- kebab case or camel case?
- Recommendation is not made on Option 3 (camelCase). 
- Discussion will be taken offline.
