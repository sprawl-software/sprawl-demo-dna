# 🌱 Sprawl Demo DNA

Welcome to the **Demo DNA Repository** for the [Sprawl CLI](https://https://github.com/w3bwizart/sprawl-cli)!

Whether you are a seasoned software engineer or someone just starting to experiment with AI coding assistants (like Claude Code or Cursor), this repository is built for you.

Think of **Sprawl** as a way to organize your AI's brain. A **DNA repository** like this one is simply a collection of instructions, rules, and personalities that you can quickly "inject" into your AI projects to make them smarter and more predictable.

This repo is a completely safe, zero-friction sandbox. It's designed to let you play with Sprawl's core features—like the `init`, `fetch-dna`, and `sync` commands—without having to build complex AI architectures from scratch.

## 📦 What's Inside?

This DNA contains five simple, harmless building blocks (which represent the core pillars of the Sprawl ecosystem):

- **Atom** (`atoms/user_profile.json`): Atoms are templates that teach your AI how to structure data. This one shows what a standard "User Profile" should look like.
- **Molecule** (`molecules/local-filesystem-mcp.json`): Molecules connect your AI to the outside world. This example gives the AI the ability to safely interact with your local computer files.
- **Persona/Skill** (`skills/persona-demo_engineer/SKILL.md`): Skills give your AI a unique personality and specific expertise. Meet the "Demo Engineer"!
- **Rule** (`rules/demo_security.md`): Rules set safe boundaries. This file teaches your AI what it can and cannot do.
- **Workflow** (`workflows/demo_build.md`): Workflows are step-by-step recipes that guide your AI to complete tasks consistently.

## 🚀 How to Try It Out

Ready to see it in action? You can securely clone this DNA into your local setup by running:

```bash
sprawl init https://github.com/w3bwizart/atomic-agentic-fabric-demo-dna.git
```

Next, create a fresh workspace (a playground for your AI) and add these demo pieces:

```bash
sprawl create my-test-workspace
cd my-test-workspace

# Mix and match the pieces you want your AI to use!
sprawl add user_profile.json local-filesystem-mcp.json demo_security.md persona-demo_engineer
```

That's it! You've just organized your AI's behavior in seconds. Dive into the files in this repository to see how human-readable and accessible they are!

## 🚀 Next Steps (Graduating the Sandbox)

Now that you've seen how Sprawl works with the Demo DNA, you are ready to create your own!

1. Delete the `my-test-workspace` folder you just made.
2. Go to your own blank Git repository.
3. Run `sprawl init <YOUR_OWN_GIT_URL>`.
4. Start writing your own rules, skills, and personas to build your private AI brain!
