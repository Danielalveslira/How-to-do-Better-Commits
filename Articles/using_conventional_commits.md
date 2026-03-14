## Using Conventional Commits

I will use **Conventional Commits** to help both: people and machines understand commits better.

Conventional Commits became very popular. So, when a project chooses a pattern for commit messages, there is a big chance that this pattern will be used.

The format is very simple.

It starts with the **type** of the commit, for example:

- `fix` for a bug fix
- `feat` for a new feature

After the type, we can have the **scope**, but this part is optional.

Then we have the **description**, and this part is required.

We can also have:

- a **body** (optional)
- a **footer** (optional)

Official website:

https://www.conventionalcommits.org/en/v1.0.0/

To get better at Conventional Commits, and write commits in a clean and nice way like many professional developers do, we need to practice a lot.

And to help us, and also make sure our commit messages follow the correct format, I will use a commit linter called **commitlint**.

Official website:

https://commitlint.js.org/

With it, we can create our own rules, our own conventions, and share them with the team. We can also use it with Git hooks and with a continuous integration flow, and this is very important.

## Let’s run it

From NPM, I will install:

https://www.npmjs.com/package/@commitlint/cli

In the terminal, I can create a new branch to add this new feature.

Then, inside this branch, I will install it as a development dependency:

```bash
npm i -D @commitlint/cli
```

Or, if I want, I can choose a specific version:

```bash
npm i -D @commitlint/cli@version
```

But there is one important detail.

Even after installing `@commitlint/cli`, we only installed the **CLI**, or the main software of commitlint. It does not come with the Conventional Commits rules by default.

And that is exactly what we want to validate.

But no problem. There is another package for that:

```bash
npm i -D @commitlint/config-conventional
```

This package gives us the Conventional Commits rules and config.

It is also a well-used package, and that is good.

## Now let’s configure it

Now that we installed the commitlint rules, we still need to tell commitlint to use them.

In the root of the project, create a file called:

```text
commitlint.config.js
```

Inside this file, add:

```js
module.exports = {
  extends: ["@commitlint/config-conventional"],
};
```

Now, if everything is right, we can start to practice in the terminal by writing commit messages in the correct way.

## Running commitlint with npx

Now let’s run the commitlint binary.

For that, we can use the `npx` command.

`npx` is used to run modules directly in the terminal.

So, when we run:

```bash
npx commitlint
```

`npx` looks for this module in the project.

- If it finds it locally, it runs it.
- If it does not find it, it can install it for a short time and run it.

In our case, it is already installed.

By default, it will show the help message with usage instructions.

## Testing commit messages 🐾

Now let’s practice.

A very nice thing is that commitlint reads from **stdin** by default.

So we can send a message to it using the `echo` command.

For example:

```bash
echo "test" | npx commitlint
```

Here, commitlint will check the message and show what is wrong.

It will say that the **subject** and the **type** cannot be empty.

![foto](https://i.imgur.com/bL40FTZ.png)

Excellent. 

Now I will repeat the command, but this time I will add a type and the main message:

```bash
echo "test: main message" | npx commitlint 
```

And look at the result:

![foto](https://i.imgur.com/p4gqiVQ.png)

```text
type must be one of [build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test] [type-enum]
```

Very nice.

Now commitlint is saying that the type must be one of those allowed types.

Now one more test. 😍

What if I write the type with an uppercase letter? Will it complain?

![foto](https://i.imgur.com/Bls2sqI.png)

Yes, it complains.

Very nice!!

## So, now everything is working.

The commit messages are being validated, and **commitlint** was added to the project successfully.

*To be continued...*