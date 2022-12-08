# Is Deno relatively unsuccessful, failing to gain traction?

Deno was supposed to be an alternative to shitty `node`, as per [their GitHub repo](https://github.com/denoland/deno):

> A modern runtime for JavaScript and TypeScript.

In other words: better, quicker and more awesome `node`.

But, something along the way went wrong, terribly wrong. Let's dive deep in.

# Situational analysis

## Cons:

*   Rust: language designed, written and (still) taken care of by employees of Mozilla. This company has the habit of making software as bad as one can imagine.
    
*   The codebase is extremely hard to maintain. Partly due to being written in Rust,
    
*   Lack of aliasing
    
*   One command can be used to invoke two (or more) separate actions
    
*   extremely resource hungry
    

## Pros

*   small ( &lt;.5MB )
    
*   full interoperability
    
*   `MIT` licensed
    

## What went wrong?

*   language: Rust is, to put it mildly, like an immature, spoiled., child. Very "noisy"; much of this noise is, in fact, a false positive that originates directly from the horrible quality of code.
    
*   lack of proper PR/Marketing campaign,
    
*   its main competitor (`node`) is too popular; by coverage, but also because core team members of `Node` are trying to eliminate any mention of `Deno` from their communication channels.
    

# Is there future for `Deno`?

Oh yes, I think so. But `Deno` core team will have to either:

*   do a full rewrite in some more normal language ( like `JavaScript` ),
    
*   step down,
    

I'm fully aware that Deno is `MIT` so anyone can fork, detach and rewrite it, but I think that it should be taken care of by the original author (would be the best solution).

All in all, answering question from the title of this article, I think that, as it is now, `Deno` **is failing.**