# Vibe Coding Your First API: How We Built LaunchPad API in Days (Not Months)

![LaunchPad API Promo](docs-graphics/promo_horizontal_en.png)

*A real-world guide for entrepreneurs who want to build their backend without hiring a developer or drowning in technical complexity*

---

## How to Use This Guide (Yes, It's Long—Here's Why That's Actually Good)

Let's be honest right up front: this guide is extensive. If you're looking for a quick "copy-paste this code and you'll have an API in 10 minutes" tutorial, you're going to be disappointed. And honestly, that's a good thing, because those quick tutorials are exactly why so many entrepreneurs end up with broken, insecure systems that cost them thousands to fix later.

### Why We Made It This Way

When I first started learning to build software, I was frustrated by the same thing you might be feeling right now. Every tutorial skipped the parts I actually needed to understand. They'd say "just run this command" without explaining why. They'd gloss over security considerations because "that's advanced stuff." They'd assume I already knew what an "ORM" was or why "middleware" matters.

I kept hitting walls where things didn't work, and I had no idea why. I'd spend hours Googling error messages that made no sense to me. I'd follow a tutorial step by step only to discover it was written for an older version of the software, and now nothing worked.

So when we wrote this guide, we made a deliberate choice: **we're going to explain everything.** Not because we think you're not smart enough to figure it out, but because you shouldn't have to. Building software is hard enough without also having to decode what the documentation assumes you already know.

This guide is long because:

- **We explain the "why" behind every decision**, not just the "what" and "how"
- **We share the mistakes we made** so you can avoid them (we made plenty)
- **We provide context** about how different pieces fit together
- **We document alternatives** we considered and why we chose what we did
- **We include troubleshooting** for the problems you'll actually encounter

### Three Ways to Read This Guide

Depending on where you are in your journey, you have three options:

**Path 1: The Deep Dive (Recommended if you have time)**

Read it from start to finish. Yes, it's long, but you'll finish with a complete understanding of not just how to build an API, but how APIs work, why they're structured the way they are, and how to troubleshoot problems when they inevitably occur. This is the path that will serve you best long-term because you'll truly understand what you're building.

**Path 2: The Strategic Skim (If you need to move fast)**

Read these sections first:
1. **This introduction** (you're here now)
2. **The Problem We All Face** – to understand if this guide is actually for you
3. **What is "Vibe Coding"?** – to understand the methodology
4. **The Technical Stack** – to understand what we're building with (skim the technical details, focus on the analogies)
5. **The Complete Architecture Overview** – to see the big picture
6. **Quick Start Guide** – to get up and running fast

Then use the rest as a reference when you need it. Come back to specific sections when you encounter those issues in your own building process.

**Path 3: The "I'm Stuck" Rescue (For when things go wrong)**

Use the table of contents to jump directly to the section that matches your current problem:
- Can't get the server running? → The Complete Installation section
- Confused about authentication? → Understanding Authentication & Shield
- Getting weird error messages? → Troubleshooting Common Issues
- Not sure if your API is secure? → Security Deep Dive
- Need to understand database structure? → Database Architecture
- Ready to deploy but don't know where to start? → Day 5: Taking Your API Live
- Getting "500 Internal Server Error" on production? → Day 5: Deployment Troubleshooting
- Database connection failing on the server? → Day 5: Production Database Setup

### What You'll Actually Build

By following this guide, you'll create LaunchPad API—a production-ready authentication and user management system that includes:

- User registration and login (with email verification)
- Secure password handling (you won't even store passwords yourself)
- API tokens for mobile app authentication
- User groups and permissions (admins, regular users, etc.)
- A complete testing framework
- Security protections against common attacks
- **Complete deployment to live hosting** (shared hosting, domain, SSL, database)
- Monitoring, backups, and maintenance setup
- Comprehensive documentation of every decision

This isn't a toy project. It's the foundation that real businesses use. When you're done, you'll have something **live on the internet** that you could actually use for a real application—not just code running on your laptop.

### The Mindset Shift That Makes This Work

Here's the thing about learning to build software: it's not about memorizing commands or syntax. It's about understanding patterns and principles. Once you understand why something works, you can apply that understanding to new situations even when the specific details change.

Think of this guide like learning to cook versus following a recipe. A recipe tells you "add 2 cups of flour and bake at 350°F for 30 minutes." Learning to cook means understanding why you're using flour (structure), why 350°F (Maillard reaction without burning), and why 30 minutes (setting proteins and starches).

We're teaching you to cook, not just follow recipes. That's why we take the time to explain the reasoning. When you understand the reasoning, you can adapt when your situation is different. When you just follow recipes, you're lost the moment something doesn't match exactly.

### A Map of What's Coming

Here's what this guide covers, in order:

**Part 1: Understanding the Landscape** (You're here)
- The problem we're solving and why existing solutions fall short
- What Vibe Coding actually means and why it works
- Why we chose the specific tools we did (PHP, CodeIgniter 4, Shield)
- The business case for building your API first (before your mobile app)

**Part 2: Setting Up Your Environment**
- Installing everything you need (PHP, Composer, database)
- Configuring your development environment
- Understanding the project structure
- Setting up version control (Git)

**Part 3: The Foundation—CodeIgniter 4**
- How the framework actually works (routes, controllers, models)
- The MVC pattern explained in human terms
- Configuration files and what they control
- Debugging and development tools

**Part 4: Authentication with Shield**
- Why authentication is so complex (and why it needs to be)
- Understanding tokens, sessions, and security
- Setting up user registration and login
- Configuring permissions and user groups
- Testing your authentication system

**Part 5: Building Real Features**
- Creating your first API endpoints
- Handling data validation and error messages
- Database design and migrations
- File uploads and image handling
- Rate limiting and performance

**Part 6: Security, CORS & The Bridge to Production**
- Security checklist and common vulnerabilities
- CORS configuration (what it is and why you need it)
- HTTPS and SSL certificates
- Environment configuration for production

**Part 7: Day 5—Taking Your API Live (Real Deployment Steps)**
- Choosing shared hosting vs. VPS (and why shared hosting wins for startups)
- Step-by-step: Preparing your app for production
- Creating and migrating your production database
- Uploading files via FTP/SFTP or Git deployment
- Configuring your domain and DNS
- Setting up free SSL certificates
- Testing everything before launch
- Monitoring, backups, and maintenance

**Part 7: Documentation & Maintenance**
- Documenting your API for other developers
- Writing tests that actually catch bugs
- Debugging production issues
- Updating dependencies safely

### The Decision to Document Everything

One more thing before we dive in: you'll notice we document every decision we made. Why PHP and not Node.js? Why CodeIgniter and not Laravel? Why this authentication approach and not that one?

We do this for three reasons:

1. **So you understand** – Knowing why helps the knowledge stick
2. **So you can decide differently** – Your situation might be different from ours. If you understand our reasoning, you can make an informed choice to do things differently
3. **So you can explain to others** – When you inevitably work with other developers (or investors, or partners), you'll be able to articulate why your system is built the way it is

We're not saying our choices are the only right choices. We're saying these are the choices we made, here's why we made them, and here's what we learned from them. Take what works for you, question what doesn't, and build something that fits your specific needs.

### Final Pep Talk (Because You'll Need It)

Building software is hard. There's no getting around that. But it's not impossible, and you don't need a computer science degree to do it. You need persistence, curiosity, and a willingness to sit with confusion until it makes sense.

You're going to hit moments where nothing works and you have no idea why. That's normal. That's part of the process. The difference between people who successfully build software and people who give up isn't intelligence—it's the willingness to keep going when things get frustrating.

This guide is here to reduce that frustration as much as possible, but it can't eliminate it entirely. Building things is inherently messy. Embrace the mess. Learn from it. And remember that every error message is just the computer trying to tell you something—it might be speaking in a foreign language right now, but by the end of this guide, you'll be fluent.

Ready? Let's build something real.

---

## The Problem We All Face

You've got the idea. You've validated it with potential customers. You can see exactly how your app will change people's lives. But then comes the wall: **the technology**.

Maybe you've been quoted $10,000-$50,000 for a "simple" backend. Maybe you've tried learning to code but got lost in tutorials that assume you already know what an "endpoint" is. Maybe you've heard you need to hire a CTO or technical co-founder, but finding the right person feels impossible when you don't even know what questions to ask.

We felt exactly the same way.

But here's what we discovered: **You don't need to become a senior developer to build production-ready software.** You need the right tools, the right approach, and an AI partner that actually understands what you're trying to do.

That's what this guide is about. We're going to show you exactly how we built LaunchPad API—a secure, scalable backend foundation—using a methodology we call **"Vibe Coding."**

## What is "Vibe Coding"?

Vibe Coding is the art of building software alongside AI, not against it. Instead of spending months learning syntax and frameworks before writing a single line of production code, you:

1. **Set up your environment** with proper documentation
2. **Train your AI assistant** on your specific tech stack
3. **Build iteratively** with AI as your pair programming partner
4. **Document everything** so your future self (and your team) understands the "why" behind every decision

Think of it like this: Traditional coding is like learning to build a house by first becoming a master carpenter, electrician, and plumber. Vibe Coding is like having an expert contractor standing next to you, handing you the right tools, explaining why we're using them, and making sure the foundation is solid.

You still learn. You still understand what you're building. But you don't get stuck in tutorial hell for six months before shipping anything.

## Meet LaunchPad API

**LaunchPad API** is our project name for a production-ready API foundation. Think of it as the engine room of a web application—the part users never see but that makes everything work.

Here's what LaunchPad API includes:

- **User Authentication**: Registration, login, password reset, secure sessions
- **API Security**: Tokens for mobile apps, permissions for different user types
- **Database Structure**: Organized, scalable data storage
- **Admin Tools**: Managing users, monitoring activity
- **Testing Framework**: Making sure everything works before users see it
- **Documentation**: Every decision explained, every command documented

We built this in days, not months. And we're going to show you exactly how, so you can do the same for your project.

## The Technical Stack: Explained Simply

![Technical Stack Flow](docs-graphics/flow_horizontal_en.png)

Before we dive into the process, let's talk about what we're actually building with. If you're completely new to this, these concepts might sound intimidating. They're not. Think of them as the ingredients in a recipe—you don't need to know organic chemistry to bake a cake.

### What is an API?

An API (Application Programming Interface) is like a waiter at a restaurant. You (the customer) don't go into the kitchen to make your own food. You tell the waiter what you want, they take that order to the kitchen, and they bring back your meal.

In software:
- Your mobile app or website is the customer
- The API is the waiter
- The database and business logic is the kitchen

The API makes sure the right requests get to the right places and that sensitive stuff (like other people's data) stays protected.

### Why Mobile Apps Absolutely Need an API (And Why This Guide Exists)

Let me paint you a picture. Imagine you've just downloaded a new fitness app on your phone. You open it up, create an account, and start logging your workouts. You can see your progress over time, compare yourself to friends, and get personalized recommendations based on your goals. It feels almost magical how everything just works.

But here's what you don't see happening behind the scenes, and it's crucial to understand this if you're building your own app:

**Your phone is actually quite limited on its own.**

Think about it. Your mobile phone has some storage space, sure. But if that fitness app stored all your workout data, all your friends' data, all the exercise libraries, and all the analytics calculations directly on your phone, a few things would happen pretty quickly:

1. **You'd run out of space** after a month of tracking
2. **You'd lose everything** if you dropped your phone in a pool
3. **You couldn't see your friends' progress** unless they physically handed you their phone
4. **The app would be impossibly slow** trying to calculate complex statistics on a tiny processor
5. **You couldn't access your data from another device** like your tablet or computer

This is where the API becomes the unsung hero of modern mobile apps.

**The Real Job of a Mobile App API**

When you tap that button to log a workout, here's what actually happens in the blink of an eye:

Your phone (the app) sends a message to the API saying something like: "Hey, this user just ran 3 miles in 28 minutes. Please save this and tell me how it compares to their previous runs."

The API receives this message, checks that you're really you (authentication), validates that the data makes sense (3 miles in 2 minutes would be suspicious), and then does the heavy lifting. It:

- Stores that workout in a secure database where it won't disappear if you lose your phone
- Calculates your average pace, calories burned, and progress trends using powerful server computers
- Checks if you've hit any milestones or personal records
- Looks up your friends' recent activities to see if anyone beat your time
- Prepares a beautiful response with all this information formatted perfectly for your phone screen

Then the API sends all that processed information back to your phone, and the app displays it in a way that looks simple and intuitive to you.

**But Why Can't the App Just Do This Directly?**

This is the question that stumped me when I first started learning about app development. Why all this back-and-forth? Why not just connect the app directly to the database?

Here's the thing: **you could, technically, but it would be a security nightmare.**

If your app connected directly to the database, that means every copy of your app floating around on thousands of phones would need to contain the database password and connection details. It would be like giving every customer at a restaurant the keys to the kitchen, the safe, and the owner's office. Sure, most people wouldn't do anything malicious, but it only takes one person to ruin everything.

The API acts as a security guard with a very specific job description. It decides:
- Who's allowed to request what data (authentication)
- What operations each person is permitted to perform (authorization)
- Whether the data being sent looks legitimate (validation)
- How much information to release and in what format (data transformation)

Without this middle layer, anyone with a little technical knowledge could potentially read other users' private information, delete entire databases, or manipulate data in ways that break your application.

**The Business Case That Made This Click for Me**

When we started planning our own app, I kept thinking: "Can't we just build the mobile app and skip the API part? Wouldn't that be faster and cheaper?"

Then a mentor asked me a series of questions that changed everything:

"What happens when you want to add a web version of your app later?"
"What if you want to let third-party developers build integrations?"
"How will you update the app logic without forcing every user to download a new version?"
"What about admin dashboards for you to manage users and see analytics?"

Each question revealed another reason why the API isn't just a technical requirement—it's a business strategy.

Without an API, your mobile app is an island. It can only do what was programmed into it when you first released it. Want to add a new feature? Every single user has to update their app through the App Store, which takes days or weeks to approve and relies on users actually clicking "Update."

With an API, your app becomes a window into a constantly evolving system. You can add features, change business logic, update algorithms, and roll out improvements instantly. The app on your users' phones stays the same, but the intelligence behind it keeps getting smarter.

**Why This Guide Focuses on Building the API First**

After months of research, conversations with developers, and frankly, some expensive mistakes, we realized something counterintuitive: **the most successful app projects start with the API, not the mobile app.**

Here's our reasoning, and why we structured this guide the way we did:

**The API is your foundation.** If you start by designing beautiful mobile screens (which is tempting because they're visual and fun), you're building a house without knowing what the ground underneath looks like. You might discover that your app design requires data structures or logic that are incredibly difficult to implement efficiently. Or worse, you might build yourself into a corner where adding features later requires rebuilding everything.

**The API forces you to think about your business logic clearly.** When you design an API endpoint for "create a new order" or "calculate shipping costs," you have to define exactly what information goes in, what processes happen, and what comes out. This clarity makes your entire application more robust. You're not just making pretty screens—you're defining how your business actually operates digitally.

**The API works for everything.** Once you have a solid API, you can build:
- A mobile app (iOS or Android)
- A web application
- A desktop application
- Integrations with other services
- Admin tools for your team
- Partner APIs for third-party developers

All of these can use the exact same backend. That's incredibly powerful. You're not rebuilding your business logic four different times for four different platforms. You build it once, correctly, and everything else just connects to it.

**Security from day one.** When you build the API first, security isn't an afterthought that you bolt on later. It's woven into the fabric of how data moves through your system. You're forced to think about authentication, authorization, data validation, and encryption from the very beginning. This is much harder (and more expensive) to retrofit later.

**Testing is easier.** APIs can be tested automatically in ways that mobile apps can't. You can write scripts that verify every endpoint works correctly, that security rules are enforced, that data is validated properly. This means by the time you start building your mobile app, you have confidence that the backend is solid. You're not wondering whether bugs are in the app or the server.

**The Mobile App Becomes Simple**

Here's the beautiful thing that happens when you have a well-designed API: building the mobile app becomes almost straightforward. The app transforms from a complex piece of software that has to handle business logic, data storage, user management, and security into something much simpler—a presentation layer.

The mobile app's job becomes:
1. Display nice screens and collect user input
2. Send that input to the API
3. Receive processed data back
4. Display it beautifully to the user

That's it. All the hard stuff—the security, the calculations, the data management, the integrations—lives in the API where it can be properly protected, tested, and maintained.

**Real Examples from Our Journey**

When we were validating our app idea, we talked to several entrepreneurs who had built mobile apps without proper APIs. Their stories were remarkably similar:

One founder told us about spending $15,000 on a beautiful iOS app that worked great... until they wanted to add an Android version. They discovered that all the business logic was embedded in the iOS code, meaning they essentially had to rebuild everything from scratch for Android. Another $15,000 gone.

Another shared how their app became slower and slower as they added features. Because everything was calculated on the phone, older devices couldn't handle the workload. They had to rewrite the entire app to move processing to a server, essentially starting over.

A third had a security scare when they realized their app was storing database credentials directly in the code. Any teenager with a jailbroken phone could have extracted those credentials and accessed their entire user database.

These aren't horror stories meant to scare you. They're honest mistakes from smart people who didn't know what they didn't know. We almost made the same mistakes ourselves. That's exactly why we decided to write this guide.

**What You're Actually Building Here**

When you follow this guide and build LaunchPad API, you're not just creating a technical backend. You're building:

- **A central brain** that can power any interface you create now or in the future
- **A security fortress** that protects your users' data and your business
- **A scalable foundation** that grows with your success rather than crumbling under it
- **A business asset** that makes your company more valuable (investors love well-architected tech)
- **Your own peace of mind** knowing that you're building on solid ground

The mobile app you build later will be better, faster, and more secure because you're taking the time to build this foundation first. And if you decide to add a web app, partner integrations, or admin tools down the road, you'll already have 80% of the work done.

This is why we start with the API. Not because it's the most exciting part (let's be honest, login screens and database tables aren't as sexy as animated mobile interfaces), but because it's the part that determines whether your app succeeds or becomes another cautionary tale about technical debt and security breaches.

By the end of this guide, you'll have an API that any mobile developer can connect to with confidence. They'll thank you for the clear documentation, the consistent responses, and the robust error handling. And you'll thank yourself when your app scales to thousands of users without breaking a sweat.

That's the power of building the foundation first.

### What is PHP?

PHP is a programming language that's been around since 1995. It powers about 77% of all websites, including giants like Facebook, Wikipedia, and WordPress.

Here's what you need to know about modern PHP (version 8.2 and up):

**It's Fast**: Modern PHP is incredibly fast—often faster than Python or Node.js for typical web tasks.

**It's Stable**: Being around for 30 years means it's battle-tested. The bugs are found and fixed. The documentation is exhaustive. The community is massive.

**It's Everywhere**: Almost every web hosting company supports PHP. Almost every developer knows it or can learn it quickly. You're never locked into a niche technology.

**It's Not Your Dad's PHP**: If you last heard about PHP in 2005, forget everything. Modern PHP has types, classes, modern syntax, and all the features you'd expect from a 2026 programming language.

### What is CodeIgniter 4?

CodeIgniter is a PHP framework. Think of a framework as a pre-built foundation for a house. Instead of pouring concrete, laying blocks, and installing plumbing from scratch, you get a solid base with the infrastructure already in place.

CodeIgniter 4 specifically:

- **Handles the Boring Stuff**: Routing (mapping URLs to code), database connections, security headers, input validation—it does this automatically
- **Enforces Good Structure**: It guides you to organize your code properly, which matters when your app grows
- **Is Lightweight**: Unlike some frameworks that feel bloated, CodeIgniter stays out of your way
- **Has Great Documentation**: The manual is clear, comprehensive, and written for humans
- **Is Modern**: Version 4 (released in 2020) brought it up to date with PHP's latest features

We chose CodeIgniter because it's the sweet spot between "too simple to be useful" and "so complex you need a PhD." It gets out of your way when you want to build, but it's there to help when you need it.

### What is Composer?

Composer is PHP's package manager. If that means nothing to you, think of it like this:

Imagine you're baking a cake, but instead of buying flour, sugar, and eggs separately, you could just say "I want a chocolate cake" and someone delivers everything you need, in the right amounts, with instructions.

That's Composer.

In the software world, developers share their solutions to common problems. Need user authentication? Someone already built that. Need to send emails? There's a package for that. Need to validate forms? Done.

Instead of writing thousands of lines of code (and introducing thousands of opportunities for bugs), you run one command:

```bash
composer require codeigniter4/shield
```

And just like that, you have a complete authentication system—user registration, login, password reset, security features, API tokens—installed and ready to go.

Composer handles:
- Downloading the code
- Downloading any code THAT code depends on
- Installing everything in the right places
- Updating everything when new versions come out
- Making sure versions don't conflict with each other

It's like having a meticulous assistant who never forgets a dependency and always reads the instructions.

### Setting Up Your Local Development Environment

Here's something that confused us for a long time: You can't just double-click a PHP file and have it run like a Word document or a spreadsheet. PHP is a server-side language, which means it needs a server to run on. Your computer needs to act like a web server, at least while you're building and testing your application locally.

Now, you could set this up manually. You could install PHP itself, then install a web server like Apache or Nginx, then install a database like MySQL, then configure them all to talk to each other. You'd spend days reading documentation, editing configuration files, troubleshooting why things aren't connecting properly, and generally fighting with your computer instead of building your application.

Or... you could use a tool that does all of this for you automatically.

**Enter local development environments like XAMPP and Laragon.**

These are specialized applications designed to turn your computer into a complete web server with a single installation. Think of them as pre-packaged kits that contain everything you need to run PHP applications locally.

**What These Tools Actually Are**

When we say "development environment," we're talking about a complete stack of software that mirrors what your application will run on when it's live on the internet. A typical PHP stack includes:

1. **The web server** (usually Apache) — This is the software that listens for requests from browsers and delivers web pages
2. **PHP itself** — The programming language interpreter that runs your code
3. **A database server** (usually MySQL or MariaDB) — Where your application stores all its data
4. **phpMyAdmin** — A visual tool for managing your database without writing SQL commands
5. **Other utilities** — Email testing tools, SSL certificate generators, log viewers

Setting up each of these components individually is like buying car parts and assembling the engine yourself when you really just want to drive to the store. Local development environments give you the fully assembled car.

**XAMPP: The Veteran**

XAMPP has been around since 2002 and is one of the most widely used local development environments. The name stands for Cross-Platform (X), Apache, MySQL, PHP, and Perl. It's maintained by Apache Friends and has been downloaded millions of times.

When you install XAMPP, you get:
- Apache web server configured and ready to go
- PHP (multiple versions available)
- MySQL database server
- phpMyAdmin for database management
- ProFTPD for file transfer
- Mercury Mail for testing email sending

XAMPP is reliable, well-documented, and battle-tested. If you run into a problem, chances are someone else has had it too and there's a solution on Stack Overflow.

**Laragon: The Modern Alternative**

Laragon is newer—it started around 2016—but it's gained a passionate following among PHP developers. We chose Laragon for this project, and here's why:

First, it's fast. Really fast. It starts up in seconds and uses minimal system resources. On a modern computer, you barely notice it's running.

Second, it's portable. You can install Laragon on a USB drive and take your entire development environment with you to any computer. This is incredibly useful if you work across multiple machines or want to show your work to someone without setting up their computer.

Third, it makes common tasks effortless. Creating a new project in Laragon is as simple as typing a name and clicking "Create." It automatically sets up the folder structure, configures the virtual host, and even creates a friendly local URL (like `myproject.test` instead of `localhost/myproject`).

Fourth, it includes modern conveniences that XAMPP lacks:
- Built-in support for HTTPS out of the box
- Easy switching between PHP versions
- Terminal integration with useful shortcuts
- Git integration
- One-click installation of popular applications (WordPress, Laravel, Symfony, etc.)

**How These Tools Enable Your Development Process**

Having a local development environment changes everything about how you build software. Here's what becomes possible:

**1. Instant Feedback Loop**

You write some code, save the file, refresh your browser, and see the result immediately. This tight feedback loop is essential for productive development. Without a local environment, you'd have to upload files to a remote server every time you wanted to test a change, adding minutes to every iteration.

**2. Safe Experimentation**

Your local environment is your sandbox. You can break things, try crazy ideas, mess up the database, delete everything, and start over—all without affecting anyone else or any live users. This freedom to experiment is crucial when you're learning and building.

**3. Offline Development**

Once your environment is set up, you don't need an internet connection to code. You can work on airplanes, in coffee shops with spotty WiFi, or anywhere. Your code, your database, your entire application lives on your computer.

**4. Database Management**

Both XAMPP and Laragon come with phpMyAdmin, a web-based interface for managing your database. Instead of learning SQL commands right away, you can:
- Browse tables visually
- Add or edit records by clicking and typing
- Run queries and see results in a formatted table
- Import and export data
- Create backups with a few clicks

This visual approach makes databases much less intimidating when you're starting out.

**5. Testing Real-World Scenarios**

A local environment lets you test things that would be dangerous or impossible on a live site:
- What happens when 10,000 users hit my API at once? (Use a load testing tool)
- How does my app behave with a million records in the database? (Generate test data)
- What if I change this core function—will everything break? (Test thoroughly before deploying)

**6. Version Control Integration**

Modern development environments integrate with Git, the version control system. This means you can:
- Track every change you make
- Revert mistakes instantly
- Create branches to experiment without affecting your main code
- Collaborate with others without stepping on each other's work

**Why We Chose Laragon for This Guide**

We actually tried both XAMPP and Laragon during this project. Both work perfectly well with CodeIgniter 4. But we kept coming back to Laragon for one simple reason: it gets out of our way.

With XAMPP, we found ourselves:
- Digging through configuration files to change PHP versions
- Manually setting up virtual hosts for each project
- Restarting the entire stack when we made configuration changes
- Dealing with permission issues on Windows

With Laragon:
- We right-clicked the system tray icon and selected a different PHP version
- It automatically created pretty URLs for each project
- Configuration changes took effect immediately without restarts
- Everything just worked on Windows

For someone learning to build APIs, these friction reductions matter. Every minute not spent troubleshooting your environment is a minute spent learning and building.

**The "It Works on My Machine" Problem**

There's a running joke in software development: "It works on my machine." This refers to the frustration when code runs perfectly on a developer's computer but fails when deployed to a server. The root cause is usually differences in configuration—different PHP versions, different extensions enabled, different server settings.

Local development environments help solve this by making your local setup as close as possible to a production server. When you eventually deploy your application, there are fewer surprises because you've been developing in an environment that mimics the real thing.

**Getting Started**

If you're following along with this guide:

1. Download Laragon from laragon.org (it's free and open source)
2. Install it—the defaults are fine for most people
3. Create a new project folder in Laragon's `www` directory
4. Visit `http://localhost` or `http://your-project.test` in your browser
5. Start coding

That's it. No complex configuration. No editing Apache config files. No troubleshooting why MySQL won't start. Just install, create, and build.

**The Bottom Line**

Before we discovered tools like Laragon, setting up a development environment felt like a barrier to entry. It was this technical hurdle you had to clear before you could even start learning. We'd spend hours following tutorials, get stuck on some obscure configuration issue, and eventually give up frustrated.

Local development environments remove that barrier. They let you focus on what you actually want to do: build your application. The infrastructure becomes invisible—just another tool that works reliably in the background while you create.

For LaunchPad API, Laragon gave us a stable, fast, easy-to-use environment where we could build and test our API locally before ever thinking about deployment. It made the technical foundation of our project feel approachable instead of intimidating.

If you're just starting out, our advice is simple: Don't try to be a system administrator and a developer at the same time. Let tools like Laragon handle the infrastructure so you can focus on building your product.

## The Hidden Danger: Why Your `.env` File Is More Important Than You Think

Let me tell you a story that keeps me up at night. A friend of mine—smart guy, successful entrepreneur—spent six months building his app. He had users, revenue, everything was going great. Then one morning, he woke up to find his entire database wiped clean. Years of customer data, gone. His business was effectively dead overnight.

What happened? He had accidentally committed his database password to GitHub. It was sitting there in plain text for anyone to see. Someone found it, logged in, and deleted everything.

This is the kind of mistake that seems impossible until it happens to you. And it's way more common than you might think. I've seen this story repeated dozens of times in developer forums, always with the same heartbreaking arc: someone didn't understand the importance of hiding their secrets, and they paid the price.

### The Problem: Code That Travels

Here's something that wasn't obvious to me when I started: **your code is going to end up in places you don't control.**

Think about the lifecycle of your application:
1. You write code on your laptop
2. You save it to GitHub (or another code repository)
3. Maybe you share access with a developer you hired
4. You deploy it to a web server
5. You might have team members downloading it to their machines
6. Eventually, you might open-source parts of it

At every single one of these steps, anyone with access can read every line of code. Every. Single. Line.

Now imagine you've written something like this in your code:

```php
$databasePassword = "SuperSecretPassword123!";
$apiKey = "sk_live_1234567890abcdef";
```

Those credentials are now everywhere your code is. Anyone who can see your code can log into your database. Anyone who can see your code can make API calls using your account (and rack up your bill). Anyone who can see your code can become you.

This isn't theoretical. I've personally seen GitHub repositories with millions of views that accidentally included Stripe API keys, AWS credentials, and database passwords. Bots scan GitHub specifically for these patterns. The moment you commit a secret to a public repository, it's compromised. Even in private repositories, you're one disgruntled employee or hacked account away from disaster.

### The Solution: Environment Variables

So how do we solve this? We need a way to configure our application without putting secrets in the code itself.

Enter the `.env` file.

An environment file is a special file that sits in your project folder but **never gets committed to your code repository**. It contains configuration values that are specific to the environment your code is running in—your laptop, your staging server, your production server.

Think of it like this: Your code is a recipe book. The `.env` file is your kitchen's pantry. The recipe (code) says "add two eggs," but it doesn't specify which eggs—you use whatever eggs are in your pantry (environment) at that moment. Different kitchens (environments) have different ingredients, but the recipe stays the same.

Here's what a typical `.env` file looks like:

```bash
# Database Configuration
database.default.hostname = localhost
database.default.database = my_app_db
database.default.username = app_user
database.default.password = SuperSecretPassword123!
database.default.DBDriver = MySQLi

# API Keys
STRIPE_SECRET_KEY = sk_live_1234567890abcdef
STRIPE_PUBLISHABLE_KEY = pk_live_0987654321fedcba

# Application Settings
app.baseURL = 'http://localhost:8080'
CI_ENVIRONMENT = development
```

Then in your code, instead of writing the actual password, you reference the environment variable:

```php
// Instead of this (BAD):
$password = "SuperSecretPassword123!";

// You do this (GOOD):
$password = getenv('database.default.password');
```

Now your code doesn't contain any secrets. It just knows how to look them up when it runs.

### Why This Matters: A Real-World Analogy

Imagine you're building a house. You wouldn't write your home address and the combination to your safe directly onto the blueprints, then hand copies of those blueprints to every contractor, inspector, and delivery person who works on your house. That's insane, right? Anyone with the blueprint could find your house and open your safe.

But that's exactly what you're doing when you hardcode secrets into your application.

Instead, the blueprint (your code) describes how to build the house, and each person gets only the information they need for their specific job. The electrician gets electrical specs, not the safe combination. The plumber gets pipe diagrams, not your WiFi password.

The `.env` file is like a secure document that stays in the house after construction. It contains all the sensitive information that the house needs to function—alarm codes, WiFi passwords, safe combinations—but it's never included in the plans that get passed around.

### The `.env` vs `.env.example` Pattern

Here's the practical workflow that professional developers use:

**1. Create a `.env.example` file**
This file contains all the configuration keys your application needs, but with placeholder values instead of real secrets:

```bash
# Copy this file to .env and fill in your real values
database.default.hostname = localhost
database.default.database = your_database_name
database.default.username = your_username
database.default.password = YOUR_PASSWORD_HERE
```

**2. Add `.env` to your `.gitignore` file**
This tells Git to never track or commit your `.env` file. It stays on your local machine only.

**3. Copy `.env.example` to `.env` on each environment**
When you set up a new developer's laptop, or deploy to a server, you copy the example file and fill in the real values.

**4. Never commit the real `.env` file**
Ever. Not even "just this once." Not even "just for testing." Never.

### What Goes in Your `.env` File?

Over time, you'll accumulate various secrets and configuration values. Here's what typically belongs in your environment file:

**Database Credentials**
- Hostname
- Database name
- Username
- Password
- Port number

**API Keys**
- Payment processors (Stripe, PayPal)
- Email services (SendGrid, Mailgun)
- Maps and geolocation (Google Maps, Mapbox)
- SMS services (Twilio)
- Cloud storage (AWS S3, DigitalOcean Spaces)
- Any third-party service you integrate with

**Application Secrets**
- Encryption keys
- Session secrets
- JWT signing keys
- CSRF tokens

**Environment-Specific Settings**
- Base URL (localhost vs production domain)
- Debug mode (on in development, off in production)
- Log levels
- Email settings (use real emails in production, fake ones in development)

### The Nightmare Scenarios We Avoided

I want to drive home how serious this is by sharing a few more stories from the real world:

**The $50,000 AWS Bill**
A startup accidentally committed their AWS access keys to a public GitHub repository. Within 24 hours, cryptocurrency miners had found the keys, spun up hundreds of expensive virtual machines, and mined Bitcoin at the startup's expense. The bill was $50,000 before AWS fraud detection caught it.

**The Database Ransom**
A developer included database credentials in code that was later open-sourced. Six months later, someone accessed the production database and held it ransom for 5 Bitcoin. The company had to pay because they didn't have proper backups.

**The GDPR Violation**
An EU-based company accidentally exposed customer data because their API keys were visible in their code. They faced massive fines under GDPR regulations and had to notify thousands of customers about the breach.

These aren't horror stories to scare you unnecessarily. They're cautionary tales that happen regularly because developers underestimate the importance of keeping secrets out of code.

### Our `.env` Strategy for LaunchPad API

In our project, we take this seriously from day one. Here's our approach:

**Step 1: Create the Example File**
We created an `.env.example` file that documents every configuration option our application needs. This serves as both documentation and a template.

**Step 2: Protect the Real File**
We added `.env` to our `.gitignore` immediately, before writing any real code. This ensures we never accidentally commit it.

**Step 3: Document the Setup Process**
In our README and documentation, we explicitly tell anyone setting up the project: "Copy `.env.example` to `.env` and fill in your values."

**Step 4: Use Different Values for Different Environments**
- Development: Uses local database, debug mode enabled, test API keys
- Staging: Uses staging database, debug mode enabled, real API keys
- Production: Uses production database, debug mode disabled, real API keys, extra security settings

**Step 5: Never Log or Display Environment Variables**
In our code, we're careful never to accidentally log or output these values. If we need to debug database connection issues, we log that the connection failed, not what password we tried to use.

### Common Mistakes and How to Avoid Them

Even experienced developers slip up sometimes. Here are the most common mistakes and how to prevent them:

**Mistake 1: "I'll add it to gitignore later"**
Problem: You create the `.env` file, write some code, commit everything, then remember to add it to `.gitignore`. Too late—it's already in your history.

Solution: Add `.env` to `.gitignore` immediately when you create the project, before creating the actual `.env` file.

**Mistake 2: "I removed it from the repo, so I'm safe"**
Problem: You committed secrets, realized your mistake, and deleted the file. But Git keeps history. Anyone can still see the old commits with your secrets.

Solution: Once committed, you must rotate (change) all the exposed credentials. Deleting the file isn't enough.

**Mistake 3: "I'm just testing, I'll use placeholder values"**
Problem: You use real credentials in development "just to test," intending to clean them up later. You forget.

Solution: Never use production credentials in development. Create separate test accounts with limited access.

**Mistake 4: "My repo is private, so I'm safe"**
Problem: Private repos can be accessed by anyone you give permissions to. Team members leave. Accounts get hacked. "Private" doesn't mean "secure."

Solution: Treat private repos the same as public ones. Keep secrets out.

**Mistake 5: "I'll encrypt the secrets in the code"**
Problem: You're still storing secrets in code, just encrypted. Anyone with the code can decrypt them.

Solution: Don't store secrets in code at all, encrypted or not. Use environment variables.

### The Decision We Made

When we started LaunchPad API, we made a non-negotiable rule: **No secrets in code. Ever.**

This wasn't just about following best practices. It was about building a foundation we could trust. When you're an entrepreneur, you have enough to worry about—marketing, sales, customer support, funding. The last thing you need is a security breach that destroys everything you've built.

By using environment variables from day one, we:
- Can share our code freely without worrying about exposing credentials
- Can deploy to different environments without changing code
- Can rotate credentials easily when needed
- Can onboard new developers without giving them access to production systems
- Can sleep at night knowing our secrets are actually secret

**Trade-offs to consider:**
- **Pros**: Security, flexibility, easier deployment, better team collaboration
- **Cons**: Slightly more complex setup, need to manage environment files on each server

This is one decision that's completely reversible (you can always change your approach later), but why risk it? Start secure, stay secure.

### Getting Started with Your `.env` File

If you're following along with this guide, here's exactly what to do:

1. **Create `.env.example`** in your project root
2. **Add all the configuration keys** your app needs, with placeholder values
3. **Add `.env` to `.gitignore`** before creating the real file
4. **Copy `.env.example` to `.env`** and fill in your real values
5. **Never commit the `.env` file`**—check twice before every commit
6. **Back up your `.env` file securely**—maybe in a password manager

Remember: Your `.env` file is the key to your kingdom. Guard it accordingly.

## Why PHP APIs Make Sense for Entrepreneurs (The Real Talk)

Let's address the elephant in the room: You've probably heard that "real" developers use Node.js, Python, or Ruby. You might be wondering if you're making a mistake choosing PHP.

Here's our perspective as entrepreneurs, not academic theorists:

### The Shared Hosting Advantage

**PHP runs on shared hosting. Node.js, Python, and Ruby generally don't.**

What's shared hosting? It's the $3-$10 per month hosting that 90% of small websites use. You upload your files via FTP, and they run. That's it.

Let's talk real numbers:

| Option | Monthly Cost | Yearly Cost | Setup Complexity |
|--------|-------------|-------------|------------------|
| Shared PHP Hosting | $3-10 | $36-120 | Upload files, done |
| VPS for Node.js/Python | $20-50 | $240-600 | Server setup, monitoring, security |
| Managed VPS | $50-150 | $600-1800 | Simpler, but expensive |

**The difference**: $564 to $1,680 per year.

That's not just money—that's your marketing budget, your design budget, your runway.

### Why VPS Costs More (And What You're Paying For)

When you use Node.js, Python, or Ruby for a web application, you generally need a VPS (Virtual Private Server). This means:

1. **You get a whole server** (virtual, but still a server)
2. **You install the operating system** (Linux, usually)
3. **You install your runtime** (Node.js, Python, etc.)
4. **You configure the web server** (Nginx or Apache)
5. **You set up process management** (PM2 for Node.js, systemd services, etc.)
6. **You handle security updates** (firewall, SSL certificates, patches)
7. **You monitor for crashes** (and restart services when they fail)
8. **You scale manually** (when traffic increases, you upgrade the server)

This is totally doable. Thousands of developers do it every day. But it's a learning curve, and it's ongoing work.

### PHP's Deployment Simplicity

With PHP on shared hosting:

1. **Upload your files** via FTP or the web interface
2. **That's it**

The hosting company handles:
- The operating system
- The web server (Apache)
- PHP installation and updates
- Security patches
- Server monitoring
- SSL certificates (usually free and automatic)

You focus on building your app, not babysitting a server.

### The Learning Curve Reality

If you're learning to code while building your business, you have limited bandwidth. Every hour spent learning server administration is an hour not spent on features your customers actually care about.

PHP hosting is designed for humans:
- cPanel or similar interfaces (point-and-click file management)
- One-click installers for common apps
- Visual database management tools
- Clear error logs you can actually read
- Support staff who can help with basic questions

### When Node.js (or Python/Ruby) Actually Wins

We're not saying PHP is always the right choice. Fair comparison matters:

**Choose Node.js/Python/Ruby when:**
- You need real-time features (chat, live updates, collaborative editing)
- You're doing heavy computational processing
- You already have a technical co-founder or team
- You're building something that specifically needs those ecosystems
- Your hosting budget is $500+/month anyway

**Choose PHP when:**
- You're building a standard web application (CRUD operations, user accounts, content management)
- You want to minimize infrastructure costs and complexity
- You need to deploy quickly and iterate often
- You might need to hand this off to another developer someday (PHP developers are everywhere)

For LaunchPad API—a standard REST API with authentication—PHP is the pragmatic choice. We can focus on building features instead of managing servers.

### The Scale Question

"But will PHP scale?"

This question usually comes from people who read tech blogs but haven't actually scaled anything yet.

Here's the truth: **Your choice of language matters less than your architecture.**

Facebook runs on PHP. Wikipedia runs on PHP. Etsy runs on PHP. Slack's backend is largely PHP. These companies serve billions of requests per day.

If you get to the point where PHP is your bottleneck, congratulations—you have a very successful business, and you can afford to optimize or rewrite that specific component.

Premature optimization is the enemy of progress. Start with what works, ship fast, and optimize when you have real users and real data showing where the problems are.

## Our 3-Step "Vibe Coding" Methodology

![Vibe Coding Process](docs-graphics/vibe_horizontal_en.png)

Now let's get into the actual process. This is how we went from "we need an API" to having a production-ready foundation in days.

### Step 1: Download the Documentation Locally

This step seems simple, but it's absolutely crucial. Here's why:

**The Problem with Generic AI Help**

Most AI coding assistants (ChatGPT, Claude, etc.) have training data that's months or years old. They know about CodeIgniter, but they might not know about CodeIgniter 4's specific features. They know about authentication, but they might suggest outdated approaches.

When you ask generic AI for help, you're rolling the dice on whether the advice is current, secure, and follows best practices.

**Our Solution: Local Documentation**

We downloaded the complete CodeIgniter 4 user guide and the Shield authentication documentation directly into our project folder. Not links—actual files sitting right there on our computer.

What we downloaded:
- The entire CodeIgniter 4 user guide (HTML documentation)
- The Shield authentication library documentation (Markdown files)
- About 50MB of comprehensive, up-to-date reference material

**Why This Matters**

By having the documentation locally:
1. **It's always available**—no internet connection needed
2. **It's the official source**—no blog posts with outdated information
3. **We can point our AI at it**—this is the game-changer
4. **We can search it instantly**—find exactly what we need

Think of it like the difference between asking a general contractor for advice versus having the actual blueprints and building codes right there in front of you while they explain.

### Step 2: Let the AI Analyze and Create Skills

This is where the magic happens. We use an AI coding assistant called **OpenCode** (you can use similar tools like GitHub Copilot, Cursor, or Claude with the right setup).

**What is OpenCode?**

OpenCode is an intelligent coding assistant that lives in your development environment. Unlike generic chatbots, it's designed to understand your specific codebase and help you write, debug, and improve your code in context.

Think of it as having a senior developer sitting next to you who:
- Never gets tired
- Knows every line of your code
- Can explain things patiently
- Won't judge you for asking "obvious" questions

**Training the AI on Our Documentation**

Here's what we did:

1. **Pointed OpenCode at our local documentation**: We told it to read the CodeIgniter user guide and Shield docs we downloaded

2. **Asked it to create "Skill Files"**: These are specialized knowledge files that teach the AI about specific areas of our project

3. **Let it organize the knowledge**: The AI analyzed thousands of pages of documentation and distilled them into practical, actionable guides

**What Came Out of This**

OpenCode created 7 skill files for us:

1. **ci4-api-development** — How to build REST API endpoints the right way
2. **ci4-shield-auth** — Authentication, tokens, permissions, and security
3. **ci4-routing-controllers** — Mapping URLs to code and organizing controllers
4. **ci4-models-database** — Working with databases and data models
5. **ci4-security** — Validation, rate limiting, protecting against attacks
6. **ci4-configuration** — Settings, environment variables, services
7. **ci4-testing** — Writing tests to make sure everything works

Each skill file contains:
- Practical code examples we can copy and modify
- Best practices from the official documentation
- Common patterns and anti-patterns
- Links back to the full documentation when we need deeper detail

**The Difference This Makes**

Now when we ask OpenCode for help, it doesn't give us generic advice. It gives us CodeIgniter 4 specific advice. It knows about Shield's authentication system. It understands our project's structure.

Example:

**Without skills:** "How do I protect an API route?"
→ Generic answer about middleware (might be wrong for our framework)

**With skills:** "How do I protect an API route using Shield's token authentication?"
→ Specific code using Shield's TokenAuth filter with proper syntax

This accuracy saves hours of debugging and prevents security mistakes that could cost us later.

### Step 3: Install Libraries with Composer

Now that our AI understands our tech stack, we started building. The first thing we needed was authentication—user registration, login, password management, API tokens for mobile apps.

**The Traditional Way**

Without Composer, we'd need to:
1. Write user registration logic (validation, database storage, email verification)
2. Write login logic (password verification, session management)
3. Write password reset logic (secure tokens, email sending)
4. Write API token generation (secure random tokens, expiration)
5. Write permission checking (who can do what)
6. Write security features (rate limiting, brute force protection)
7. Test all of this thoroughly
8. Maintain it forever

That's weeks of work. And since we're not security experts, we'd probably introduce vulnerabilities.

**The Composer Way**

We ran one command:

```bash
composer require codeigniter4/shield
```

And we got all of that, immediately:

- User registration with email validation
- Secure login with password hashing (Argon2id—military-grade encryption)
- Password reset via secure tokens
- Session management
- API access tokens with scopes and expiration
- HMAC authentication for high-security endpoints
- Group-based permissions (admin, user, etc.)
- Rate limiting to prevent brute force attacks
- CLI commands to manage users
- Complete database migrations (creates all necessary tables)

**Setup took 5 minutes.**

After installation:
1. Shield created configuration files for us
2. We ran the migrations to set up database tables
3. We configured a few settings (like token expiration time)
4. Authentication was ready to use

**Real Example: Creating a Protected API Endpoint**

Here's actual code from our project. Don't worry if you don't understand every symbol—we'll explain:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class UserController extends ResourceController
{
    // This connects to our UserModel for database operations
    protected $modelName = 'App\Models\UserModel';
    
    // We want JSON responses by default
    protected $format = 'json';

    /**
     * Get a list of all users
     * GET /api/users
     */
    public function index()
    {
        // Fetch all users from the database
        $users = $this->model->findAll();
        
        // Return them as a JSON response
        return $this->respond([
            'status' => 200,
            'data' => $users
        ]);
    }

    /**
     * Get a specific user by ID
     * GET /api/users/{id}
     */
    public function show($id = null)
    {
        // Try to find the user
        $user = $this->model->find($id);
        
        // If no user found, return 404 error
        if (!$user) {
            return $this->failNotFound('User not found');
        }
        
        // Return the user data
        return $this->respond([
            'status' => 200,
            'data' => $user
        ]);
    }
}
```

And to protect this endpoint so only logged-in users can access it, we add one line to our routes:

```php
// routes.php
$routes->group('api', ['filter' => 'tokens'], function($routes) {
    $routes->resource('users');
});
```

That `['filter' => 'tokens']` tells CodeIgniter: "Hey, before letting anyone access these routes, check if they have a valid API token."

Shield handles everything else—checking the token, verifying it's not expired, loading the user, making them available in our controller.

**This is the power of Vibe Coding with good libraries.** We wrote maybe 20 lines of custom code and got a fully functional, secure API endpoint.

## The Bridge Between Your API and the World: Understanding CORS

So you've built your API. You've got authentication working. Your endpoints are responding beautifully when you test them from your own computer. Everything seems perfect.

Then you try to connect your mobile app—or your friend's web application—and suddenly nothing works. The browser shows scary red error messages. Your app throws mysterious "Network Error" exceptions. You start questioning everything you just built.

Welcome to one of the most frustrating experiences in API development. We've been there. Let us save you the three days of confusion we went through.

### The Scenario That Breaks Everyone's Heart

Picture this: You've just finished your API. You're proud of it. You open up your web browser, navigate to `http://localhost:8080/api/users`, and you see beautiful JSON data flowing back. "Perfect!" you think.

You open your mobile app code—or maybe you have a simple HTML file with some JavaScript—and you write what seems like the most straightforward code in the world:

```javascript
fetch('http://localhost:8080/api/users')
  .then(response => response.json())
  .then(data => console.log(data));
```

It should work, right? You're asking the exact same URL, expecting the exact same data. But instead of your beautiful JSON, you get an error that looks something like:

> "Access to fetch at 'http://localhost:8080/api/users' from origin 'http://localhost:3000' has been blocked by CORS policy."

Or maybe your mobile app just silently fails, or shows "Network Error" without any helpful details.

What just happened? Your API is working perfectly. Your code looks correct. Yet the two refuse to talk to each other. It's maddening.

### The Security Rule Nobody Told You About

Here's what's actually happening—and it's not a bug, it's a security feature that was added to web browsers years ago to protect you and your users.

Imagine you're logged into your bank's website in one browser tab. Then you visit another website—let's say it's a seemingly innocent news site. Without certain protections, that news site could include JavaScript code that makes requests to your bank's website using your existing login session. It could potentially transfer money, change your address, or do all sorts of malicious things using your authenticated session.

That would be catastrophic.

So web browsers implemented a rule called the **Same-Origin Policy**. This rule says: "Code running on one website can only make requests to that same website." If you're on `myapp.com`, you can talk to `myapp.com/api/users` all day long. But if you try to talk to `bank.com` from `myapp.com`, the browser steps in and says "Nope, not allowed."

This rule has saved countless people from cross-site scripting attacks and session hijacking. It's genuinely important.

But here's the problem: your API and your frontend are technically different "origins" (different ports, or different domains), so the browser treats them as different websites and blocks the communication.

### Enter CORS: The Permission Slip for Cross-Origin Requests

CORS stands for **Cross-Origin Resource Sharing**. Think of it as a formal permission system. Your API can tell browsers: "It's okay if these specific websites talk to me. I trust them."

Without CORS configuration, your API is like a house with all the doors locked. The security is great, but nobody can visit. With CORS, you can unlock specific doors for specific visitors while keeping the rest of the house secure.

The way it works is actually quite elegant. When your JavaScript code tries to make a request to a different origin, the browser first sends what's called a "preflight request." This is basically the browser asking your API: "Hey, this website at origin X wants to talk to you. Is that allowed?"

Your API responds with CORS headers that say things like:
- "Yes, origin X is allowed"
- "They can use these HTTP methods: GET, POST, PUT, DELETE"
- "They can send these headers: Content-Type, Authorization"
- "They can include credentials like cookies if needed"

Only after receiving this permission does the browser actually send the real request with your data.

### Why Mobile Apps Face This Too

You might be thinking: "But I'm building a mobile app, not a website. Why do I care about browser security rules?"

Great question. Modern mobile apps are often built using web technologies—React Native, Flutter, Ionic, or even just embedded web views. These frameworks use the same underlying browser engines to make HTTP requests. So even though your app is running on a phone, not in a web browser window, the same CORS rules apply because the networking layer is browser-based.

Additionally, during development, you're probably testing your mobile app in a browser anyway (using tools like browser-based simulators). And when you eventually build a web dashboard for your users, you'll definitely need CORS configured.

The bottom line: CORS is non-negotiable for modern API development. You need to configure it properly, and you need to understand what you're doing so you don't accidentally open security holes.

### How We Configure CORS in CodeIgniter 4

CodeIgniter 4 actually makes this relatively painless once you know what to do. The framework includes a CORS module that's built-in but needs to be enabled and configured.

Here's the decision process we went through:

**First decision: Which origins should we allow?**

In production, you want to be very specific. If your frontend runs on `https://myapp.com`, you should only allow that origin. Not `http://myapp.com` (without HTTPS), not `https://www.myapp.com` (with www), not wildcards that would let any website talk to your API.

For development, we needed to allow multiple origins because:
- Our mobile app running on a simulator might come from `http://localhost:8100`
- Our web frontend might run on `http://localhost:3000`
- Our API testing tools (like Postman or Insomnia) might not send an origin at all

**Second decision: Which HTTP methods should we support?**

For a REST API, you typically need:
- `GET` for reading data
- `POST` for creating data
- `PUT` or `PATCH` for updating data
- `DELETE` for removing data
- `OPTIONS` for the preflight requests (browsers send this automatically)

**Third decision: Which headers should we allow?**

At minimum, you need:
- `Content-Type` (so we can send JSON)
- `Authorization` (so we can send bearer tokens)
- `X-Requested-With` (used by many AJAX libraries)

**Fourth decision: Should we allow credentials?**

If you're using cookies or session-based authentication, you need to allow credentials. For token-based APIs (which is what Shield uses), you technically don't need cookies, but allowing credentials doesn't hurt and makes your API more flexible for future use cases.

### The Configuration That Actually Works

After experimenting (and failing multiple times), here's the configuration that worked for us. We created a CORS configuration file in `app/Config/Cors.php`:

```php
<?php

namespace Config;

use CodeIgniter\Config\BaseConfig;

class Cors extends BaseConfig
{
    // During development, we allow multiple localhost ports
    // In production, this should be your exact domain
    public array $allowedOrigins = [
        'http://localhost:3000',     // React/Vue dev server
        'http://localhost:8100',     // Ionic/Cordova apps
        'http://localhost:8080',     // Other local testing
        'http://localhost',          // General local development
    ];
    
    // Allow all origins with a wildcard (NOT for production!)
    // Only use this for rapid prototyping, never in production
    public bool $allowAnyOrigin = false;
    
    // HTTP methods our API supports
    public array $allowedMethods = [
        'GET',
        'POST',
        'PUT',
        'DELETE',
        'OPTIONS',
        'PATCH'
    ];
    
    // Headers the client is allowed to send
    public array $allowedHeaders = [
        'Content-Type',
        'Authorization',
        'X-Requested-With',
        'Accept',
        'Origin'
    ];
    
    // Headers the client is allowed to read from the response
    public array $exposedHeaders = [];
    
    // Whether to allow cookies/credentials
    public bool $allowCredentials = true;
    
    // How long browsers can cache the preflight response (in seconds)
    // 7200 = 2 hours, reduces preflight requests
    public int $maxAge = 7200;
}
```

Then we enabled the CORS filter in `app/Config/Filters.php`:

```php
public array $aliases = [
    'csrf'     => CSRF::class,
    'toolbar'  => DebugToolbar::class,
    'honeypot' => Honeypot::class,
    'cors'     => \CodeIgniter\Filters\Cors::class, // Add this line
];

public array $globals = [
    'before' => [
        'cors', // Apply CORS to all routes
        // ... other filters
    ],
    'after' => [
        // ...
    ],
];
```

### The Moment of Truth: Testing Your CORS Setup

After configuring CORS, you need to test it properly. Here's what we learned:

**Testing from a browser:**
Open your browser's developer console and try making a fetch request to your API from a different origin. You should see the request succeed without CORS errors.

**Testing from curl:**
```bash
# Test preflight request
curl -X OPTIONS -H "Origin: http://localhost:3000" \
  -H "Access-Control-Request-Method: POST" \
  -H "Access-Control-Request-Headers: Content-Type" \
  -I http://localhost:8080/api/users

# You should see headers like:
# Access-Control-Allow-Origin: http://localhost:3000
# Access-Control-Allow-Methods: GET, POST, PUT, DELETE, OPTIONS, PATCH
```

**Common mistakes we made:**
1. Forgetting to restart the server after changing configuration
2. Using `*` (wildcard) for origins in production (security risk!)
3. Not including the `OPTIONS` method in allowed methods
4. Forgetting to allow the `Authorization` header (breaks token auth)
5. Testing from `file://` URLs (browsers treat these differently)

### The Production Checklist

When you're ready to deploy to production, update your CORS configuration:

```php
public array $allowedOrigins = [
    'https://myapp.com',      // Your production domain
    'https://www.myapp.com',  // Include www variant
    'https://admin.myapp.com', // If you have a separate admin panel
];

public bool $allowAnyOrigin = false; // Never true in production!
```

**Why be so restrictive?**

Imagine you allow any origin (`*`) in production. Now any website on the internet can make requests to your API from their users' browsers. They could:
- Harvest data from your public endpoints
- Attempt to brute force authentication using your login endpoint
- Flood your API with requests from thousands of users

By restricting to specific origins, you ensure that only your legitimate applications can communicate with your API.

### Why This Matters More Than You Think

CORS errors are often the first real "wall" that beginner API developers hit. You've built something that works perfectly in isolation, but the moment you try to integrate it with a real frontend, everything breaks. It's demoralizing.

But here's what we've learned: CORS isn't just a technical hurdle to overcome. It's a fundamental part of web security architecture. Understanding CORS means understanding how web security works. It means thinking about which applications should have access to your data and which shouldn't.

When you configure CORS properly, you're not just fixing an error—you're making a conscious security decision about who can talk to your API and how. That's the difference between someone who "made it work" and someone who understands what they're building.

For LaunchPad API, CORS configuration was the bridge that connected our backend to the outside world. It transformed our API from a lonely island into a service that could power web apps, mobile apps, and third-party integrations. And once we understood it, it wasn't scary anymore—it was just another security layer that we controlled.

## Day 5: Taking Your API Live—Real Deployment Steps That Actually Work

So you've built your API. You've tested it locally. Everything works beautifully on your computer. Now comes the moment of truth: getting it onto the internet where real people can use it.

This is where a lot of guides leave you hanging. They say "deploy to production" like it's a single button you push, then move on to the next topic. But here's the reality: deployment is a series of decisions and steps that can make or break your project's launch. Do it wrong, and you'll spend your first week fighting configuration issues instead of celebrating your launch.

We learned this the hard way. Our first deployment attempt was... let's call it "educational." We broke things. We had to roll back. We stayed up until 3 AM wondering why something that worked perfectly on our laptop refused to work on the server. But we got through it, and now we're going to save you that pain.

### The Mindset Shift: From "It Works on My Machine" to "It Works Everywhere"

Before we dive into the specific steps, let's talk about the fundamental challenge of deployment: your production environment is different from your development environment. Different server software, different file paths, different security rules, different everything.

Think of it like this: you've been practicing a song on your acoustic guitar in your bedroom. Now you're performing it on stage with a full band, professional sound system, and a live audience. The song is the same, but everything around it has changed.

Your job during deployment isn't just to move files from one place to another. It's to adapt your application to its new home while keeping the core functionality intact. This means understanding what needs to change (configuration) and what must stay exactly the same (your code logic).

### Why We Chose Shared Hosting (And Why You Probably Should Too)

Remember back when we talked about PHP's advantages? Here's where it pays off big time. While developers using Node.js or Python are struggling with VPS configuration, server management, and deployment pipelines, you're going to upload some files and be done.

**But let's be clear about what shared hosting actually means:**

Shared hosting is like renting an apartment in a large building. You get your own space (disk space, database, email accounts), but you're sharing the building's infrastructure (the server hardware, internet connection, security systems) with other tenants. The building management (your hosting company) takes care of maintenance, security updates, and keeping things running.

**Here's why this is perfect for LaunchPad API:**

1. **Cost**: $3-10 per month versus $20-50+ for a VPS
2. **Simplicity**: No server administration required
3. **Support**: Most shared hosts have 24/7 support for basic issues
4. **Features**: You usually get email, databases, SSL certificates, and more included
5. **Scalability**: When you outgrow shared hosting, you'll have revenue to afford better options

**The trade-offs:**
- You don't have root access (can't install arbitrary software)
- Performance can vary based on what other sites on the server are doing
- You're limited to what the host provides (PHP versions, extensions, etc.)

For a new API with zero users, these trade-offs are completely acceptable. You're not going to hit performance limits with your first hundred users. And by the time you do, you'll have the revenue and knowledge to upgrade.

### Step 1: Choosing Your Hosting Provider (The Decision That Matters More Than You Think)

There are hundreds of shared hosting companies. Here's how to choose without going crazy:

**What you actually need:**
1. PHP 8.1 or higher (8.2+ preferred)
2. MySQL or MariaDB (both work fine)
3. cPanel or similar control panel (makes management easier)
4. Free SSL certificate (essential for HTTPS)
5. FTP or SFTP access (to upload files)
6. phpMyAdmin (to manage your database visually)
7. Reasonable support (24/7 chat is ideal)

**Popular options that work well:**
- **Namecheap**: Cheap, reliable, good for beginners
- **Hostinger**: Good performance, affordable, modern interface
- **Bluehost**: Popular, WordPress-friendly (which means PHP-friendly)
- **SiteGround**: Excellent support, slightly pricier but worth it for the peace of mind
- **A2 Hosting**: Developer-friendly, good performance

**What we chose and why:**
We went with Namecheap for our first deployment. Not because it's the best in every category, but because it checked all our boxes at a price point ($3.88/month) that made it easy to say yes. Their cPanel interface is standard, their support is decent, and they don't nickel-and-dime you for basic features.

**The decision process:**
- We looked at 10+ hosts
- Eliminated any without PHP 8.1+ support
- Eliminated any charging extra for SSL certificates
- Chose the cheapest option that met our technical requirements
- Planned to upgrade later if needed

**Reversible?** Absolutely. If your host disappoints, you can move your entire site in a few hours once you know the process. Don't overthink this decision.

### Step 2: Preparing Your Application for the Real World

Before uploading anything, you need to make some changes to your code. These aren't optional—they're the difference between a working API and a broken one.

**The Environment Configuration Dance:**

Remember your `.env` file? The one with all your secrets? That file lives only on your local machine. Never upload it. But your production server needs those same configuration values—just with different values (production database, production API keys, etc.).

Here's the process:

1. **Create a production `.env` file locally** (don't commit this either):
   ```bash
   # .env.production (this is just a template, rename to .env on the server)
   CI_ENVIRONMENT = production
   app.baseURL = 'https://yourdomain.com'
   
   # Production database (you'll get these from your hosting control panel)
   database.default.hostname = localhost
   database.default.database = yourhosting_username_dbname
   database.default.username = yourhosting_username
   database.default.password = your_production_password
   database.default.DBDriver = MySQLi
   ```

2. **Update your production settings:**
   ```bash
   # In .env.production
   CI_ENVIRONMENT = production
   app.baseURL = 'https://yourdomain.com'
   
   # Turn off debugging in production
   CI_DEBUG = false
   
   # Configure error logging
   logger.threshold = 4
   ```

3. **Set proper file permissions locally** (so they transfer correctly):
   Your `writable/` folder needs to be writable by the web server. This is handled differently on different hosts, but generally:
   - Folders: 755 (rwxr-xr-x)
   - Files: 644 (rw-r--r--)
   - `writable/` folder: 775 (rwxrwxr-x)

**Why this matters:**
- Production mode disables debug output (security)
- Production database credentials are different (security)
- Proper permissions prevent "permission denied" errors
- Your base URL affects how links and redirects work

**Common mistake to avoid:**
Don't just copy your local `.env` file to production. Your local database is named something like `ci_api_db`. Your production database will be named something like `namecheap_username_cidb` with a different username and password. Using local credentials on production will fail.

### Step 3: Setting Up Your Production Database

This is the part that intimidates people, but it's actually straightforward once you see it done.

**Creating the Database:**

1. **Log into your hosting control panel** (cPanel, Plesk, or whatever your host uses)
2. **Find "MySQL Databases" or "Database Wizard"**
3. **Create a new database**:
   - Name it something descriptive (yourapp_db)
   - The host usually prefixes it with your username (username_yourapp_db)
4. **Create a database user**:
   - Choose a strong password (use a generator)
   - Save this password somewhere secure
5. **Add the user to the database** with "All Privileges"

**Moving Your Local Data to Production:**

You have two options here, and we recommend the second one for beginners:

**Option 1: Export and Import (More Control):**
1. Export your local database (using phpMyAdmin, TablePlus, or command line):
   ```bash
   # If you have MySQL locally
   mysqldump -u root -p ci_api_db > backup.sql
   ```
2. Open your hosting's phpMyAdmin
3. Select your production database
4. Click "Import" and upload your backup.sql file

**Option 2: Run Migrations Fresh (Cleaner):**
1. Don't export data from local development
2. Upload your code (next step)
3. SSH into your server or use the hosting's terminal
4. Run migrations fresh on production:
   ```bash
   cd /path/to/your/app
   php spark migrate --all
   ```

**Why we prefer Option 2:**
- Cleaner database structure
- No test data polluting production
- Ensures migrations actually work
- Easier to reproduce if you need to set up staging later

**The Only Data You Might Want to Migrate:**
If you created admin users or essential configuration data locally, export just those specific tables or rows. Don't bring over test users, dummy data, or your personal testing sessions.

### Step 4: Uploading Your Files (The Moment of Truth)

Now you're ready to move your code to the server. You have a few options here.

**Understanding Your Hosting's File Structure:**

Shared hosts typically have a structure like this:
```
/home/username/           <- Your home directory (you start here in FTP)
├── public_html/          <- Web root (files here are publicly accessible)
├── mail/                 <- Email storage
├── logs/                 <- Server logs
└── .cpanel/              <- Control panel stuff
```

The `public_html/` folder is crucial. Files in here are accessible to anyone on the internet. Files outside of it (like your `.env` file, if you put it in the right place) are protected.

**Upload Method 1: FTP/SFTP (Easiest for Beginners):**

1. **Download an FTP client** (FileZilla is free and works great)
2. **Get your FTP credentials from your hosting control panel**
3. **Connect to your server**
4. **Navigate to the public_html folder**
5. **Upload your files**

**The CodeIgniter 4 Way:**
CI4 has a specific structure. Your `public/` folder needs to map to the host's `public_html/`. Here's how:

1. Upload everything EXCEPT the `public/` folder to `/home/username/ci_api/`
2. Upload the CONTENTS of your `public/` folder to `/home/username/public_html/`
3. Edit `/home/username/public_html/index.php` to point to the right place:
   ```php
   // Change this line
   $pathsPath = FCPATH . '../app/Config/Paths.php';
   // To this (adjust path as needed)
   $pathsPath = '/home/username/ci_api/app/Config/Paths.php';
   ```

**Upload Method 2: Git Deployment (If Your Host Supports It):**

Some hosts let you deploy via Git. This is cleaner but requires SSH access:
```bash
# On your server
 git clone https://github.com/yourusername/yourrepo.git
 cd yourrepo
 composer install --no-dev
 php spark migrate
```

**Upload Method 3: File Manager (No Software Required):**

Most hosting control panels have a web-based file manager. You can:
1. Zip your project locally
2. Upload the zip via the file manager
3. Extract it on the server
4. Move files to the right places

**What we did:**
We used FTP with FileZilla for our first deployment. It's visual, you can see what's happening, and if something fails, you know exactly where. As we got more comfortable, we switched to Git deployment for updates.

**Pro tip:** Upload takes a while. Get it started, make some coffee, and come back. Don't sit there watching progress bars.

### Step 5: Configuring Your Domain (Making It Official)

If you bought your domain from the same company as your hosting, this is automatic. If not, you need to connect them.

**How Domain Names Actually Work (The Simple Version):**

When someone types `yourdomain.com` into their browser:
1. Their computer asks a DNS server "What's the IP address for yourdomain.com?"
2. The DNS server looks it up and returns something like `192.168.1.100`
3. Their browser connects to that IP address
4. Your hosting server says "Hi! You want yourdomain.com? Here's the website."

**Setting Up Your Nameservers:**

1. **Find your hosting's nameservers** (usually in your welcome email or control panel)
   - They look like: `ns1.yourhost.com` and `ns2.yourhost.com`
2. **Log into wherever you bought your domain** (Namecheap, GoDaddy, Google Domains, etc.)
3. **Find the "Nameservers" or "DNS" section**
4. **Change the nameservers to your host's**
5. **Wait** (this can take anywhere from 15 minutes to 48 hours to propagate)

**Why does it take so long?**
DNS is like a giant distributed phone book. When you change nameservers, you're telling the phone book operators to update their records. Some check for updates frequently (minutes), others less frequently (hours or days). Be patient.

**Testing if it's working:**
```bash
# Use dig or nslookup to check
 dig yourdomain.com
 
# Or just visit it in a browser
# If you see your site, it's working!
```

**The "It's Been 2 Hours and Nothing Works" Checklist:**
1. Clear your browser cache (Ctrl+Shift+R or Cmd+Shift+R)
2. Try a different browser
3. Try accessing from your phone (different network)
4. Use a tool like https://dnschecker.org/ to see if it's propagated globally
5. Check that you didn't misspell the nameservers

### Step 6: Setting Up SSL (The Lock Icon That Makes You Look Professional)

HTTPS isn't optional anymore. Browsers warn users about "insecure" sites. Google ranks HTTPS sites higher. You need SSL.

**The Good News:**
Most shared hosts offer free SSL certificates through Let's Encrypt. Setup is usually:

1. **Log into your hosting control panel**
2. **Find "SSL/TLS" or "Security" or "Let's Encrypt"**
3. **Click "Install" or "Enable"**
4. **Select your domain**
5. **Wait 5-10 minutes**

**What happens behind the scenes:**
The hosting company requests a certificate from Let's Encrypt (a nonprofit that provides free SSL). Let's Encrypt verifies you control the domain by checking your nameservers. Once verified, they issue the certificate. Your host installs it automatically.

**After SSL is active:**
1. Update your `.env` file:
   ```bash
   app.baseURL = 'https://yourdomain.com'
   ```
2. Test by visiting `https://yourdomain.com` (note the https://)
3. You should see a lock icon in your browser

**Common SSL Issues:**
- **Mixed content warnings**: You're loading HTTP resources on an HTTPS page. Update all your URLs to use https://
- **Certificate not trusted**: The certificate is still propagating. Wait an hour and try again.
- **Domain mismatch**: The certificate is for www.yourdomain.com but you're accessing yourdomain.com (or vice versa). Most hosts fix this automatically, but sometimes you need to specify both.

### Step 7: The Final Tests (Before You Tell Anyone)

Don't announce your launch yet. Test everything first.

**The Smoke Test Checklist:**

1. **Homepage loads**: Visit `https://yourdomain.com`—do you see something? Anything?
2. **API endpoints work**: Test a simple GET endpoint
   ```bash
   curl https://yourdomain.com/api/users
   ```
3. **Authentication works**: Try to register a new user
4. **Database is connected**: Can you create/read data?
5. **Error handling works**: Try accessing a non-existent endpoint. Do you get a proper 404 or a server error?
6. **HTTPS is forced**: Try visiting `http://yourdomain.com` (without the s). Does it redirect to https?

**Common First Deployment Issues:**

**"500 Internal Server Error"**
- Check your `.env` file exists and has correct values
- Check file permissions (especially `writable/` folder)
- Check your host's error logs (in cPanel)
- Enable CI4's error logging temporarily to see the real error:
  ```bash
  CI_DEBUG = true  # Only temporarily!
  ```

**"Database connection failed"**
- Wrong database credentials in `.env`
- Database user doesn't have proper privileges
- Database doesn't exist (did you create it in cPanel?)
- Wrong hostname (some hosts use something other than "localhost")

**"404 Not Found on all routes"**
- Your `.htaccess` file isn't uploaded or is wrong
- mod_rewrite isn't enabled (ask your host)
- Your `public/` folder files are in the wrong place

**"CORS errors"**
- Update your `Cors.php` config to allow your production domain
- Restart your server (some configs cache)

### Step 8: Monitoring and Maintenance (Keeping It Alive)

Your API is live! But the work isn't done. You need to keep an eye on it.

**What to Monitor:**

1. **Uptime**: Is the server responding? (Most hosts provide this)
2. **Error logs**: Are there errors you didn't catch in testing?
3. **Performance**: Is it slow? (Use tools like GTmetrix or Pingdom)
4. **Security**: Any suspicious activity?

**Where to Find Logs:**

Most shared hosts provide:
- **Error logs**: cPanel → Metrics → Errors
- **Access logs**: cPanel → Metrics → Raw Access
- **Application logs**: In your `writable/logs/` folder

**Setting Up Basic Monitoring:**

Free tools that work great:
- **UptimeRobot**: Checks if your site is up every 5 minutes. Free plan covers 50 monitors.
- **Google Search Console**: Tells you about indexing issues and security problems
- **Your hosting's built-in stats**: Usually found in cPanel

**Backup Strategy (Don't Skip This):**

Most hosts do automated backups, but you should too:

1. **Database backups**: Export your database weekly
2. **File backups**: Download your entire site monthly
3. **Version control**: Keep your code in Git (you should already be doing this)

**Setting Up Automated Backups:**
Many hosts offer automated backup services (sometimes paid). If you want to do it yourself:

```bash
# Add this to your local machine as a weekly cron job
 mysqldump -h yourhost.com -u username -p'password' database_name > backup_$(date +%Y%m%d).sql
```

### The Launch Day Itself

You've done the work. Now it's time to flip the switch.

**The Soft Launch Approach:**
Instead of announcing to the world immediately, try this:

1. **Deploy a day early**: Give yourself time to fix issues
2. **Test with a small group**: Ask 2-3 friends to try it
3. **Monitor for 24 hours**: Make sure it's stable
4. **Then announce**: Share with your actual audience

**The Launch Day Checklist:**
- [ ] Site loads correctly
- [ ] SSL certificate is active
- [ ] API endpoints respond
- [ ] Authentication works
- [ ] Mobile app (if applicable) connects successfully
- [ ] Error handling works
- [ ] Database is saving data
- [ ] Backups are configured
- [ ] Monitoring is active
- [ ] Documentation is updated with production URLs

**When Things Go Wrong (And They Might):**

Here's the truth: something will break. Maybe not today, maybe not this week, but eventually. The difference between a stressful launch and a calm one is preparation.

**Have these ready:**
1. **Rollback plan**: Know how to revert to the previous version quickly
2. **Support contact**: Your hosting's support number or chat
3. **Error logs access**: Know where to find them
4. **Emergency contact**: Someone technical who can help if you're stuck

### Decision: Shared Hosting vs. VPS for Initial Deployment

**Date**: February 17, 2026
**Context**: Choosing deployment infrastructure for LaunchPad API

**Options Considered**:
1. Shared hosting ($3-10/month)
2. VPS like DigitalOcean or Linode ($20-50/month)
3. Platform-as-a-Service like Heroku (free tier available, but scales expensive)
4. Cloud hosting like AWS/GCP (overkill and complex)

**Decision**: Shared hosting for initial launch, with clear criteria for when to upgrade

**Rationale**:
- **Shared hosting**: Perfect for 0-1000 users. No server management. Cheap. Easy.
- **VPS**: Better performance and control, but requires Linux administration knowledge we don't have yet
- **PaaS**: Convenient but gets expensive fast ($25+/month for production workloads)
- **Cloud**: Massive overkill. We'd spend more time learning AWS than building our product.

**Upgrade triggers** (when we'll consider moving to VPS):
- Consistently hitting resource limits
- Need for custom server software
- Revenue justifies the extra cost
- We have time to learn server administration

**Trade-offs**:
- **Pros**: Affordable, zero maintenance, quick setup, perfect for validation phase
- **Cons**: Limited control, shared resources, can't install arbitrary software

**Reversible?** Yes. Moving from shared hosting to VPS is a common growth path. CI4 makes it relatively painless since the application code doesn't change—just the server configuration.

### Your API Is Live. Now What?

Deployment isn't the end of the journey—it's the beginning. Your API is now a living thing that needs care and feeding.

But here's the beautiful thing: you've built something real. You took an idea, learned the technology, wrote the code, and put it on the internet where anyone can use it. That's not trivial. That's impressive.

The deployment process we just walked through is something many developers never fully understand. They use automated platforms that hide the complexity, then panic when something goes wrong. You now understand every piece: the files, the database, the domain, the SSL, the whole stack.

That knowledge is power. It means when something breaks, you know where to look. When you need to scale, you know what to upgrade. When someone asks "how does your API work?" you can explain it from the ground up.

Welcome to the production world. Your API is live. Your users are waiting. Go make something amazing.

## The Art of Talking to AI: A Practical Guide to Prompt Engineering

![LaunchPad API Cover](docs-graphics/cover_horizontal_en.png)

Here's something that took us a while to figure out: **The way you ask AI for help matters just as much as having good documentation.** It's like the difference between asking a skilled contractor "Build me a house" versus "Build me a three-bedroom house with an open floor plan, using sustainable materials, designed for a family with young children." Same person, wildly different results.

When we first started using AI assistants, we made a classic mistake. We'd type things like:
- "Make this work"
- "Fix this code"
- "How do I do authentication?"

And we'd get... okay-ish results. Sometimes the code worked. Sometimes it was outdated. Sometimes it was technically correct but completely wrong for our specific situation. We spent hours debugging issues that could have been avoided if we'd just asked better questions.

### Why Prompt Engineering Isn't Just "Being Specific"

You might think prompt engineering means using fancy technical terms or writing essays to the AI. It's not. It's about giving the AI context so it can give you relevant answers instead of generic ones.

Think of it like this: If you walk into a restaurant and say "I'm hungry," the waiter has no idea whether to bring you a salad or a steak. But if you say "I'm hungry, I'm vegetarian, I love spicy food, and I'm in a hurry," now they can recommend the perfect dish.

AI works the same way. The more context you provide about:
- What you're trying to accomplish (the goal)
- What constraints you have (the boundaries)
- What you've already tried (the history)
- What your project looks like (the context)

...the better the AI can help you.

### The Framework We Use for Every Prompt

After weeks of trial and error, we developed a simple framework that dramatically improved the quality of AI assistance. We call it the **ACTS Framework** (because every acronym needs a fancy name, apparently):

**A - Assign a Role**
**C - Clarify the Context**
**T - Specify the Task**
**S - Set the Standards**

Let me break down what each of these means with real examples from our project.

#### A - Assign a Role

This is the magic ingredient that most people skip. When you tell the AI to "act as" something specific, it shifts its entire perspective and knowledge base to serve that role.

**Instead of:** "How do I create an API endpoint?"

**Say:** "Act as a senior CodeIgniter 4 developer with 10 years of experience building secure REST APIs. I'm building an endpoint for user registration."

See the difference? The first prompt gets you a generic answer that might work in any framework. The second prompt tells the AI to draw on its knowledge of CodeIgniter specifically, REST API best practices, and security considerations—all things we care deeply about.

**Other role examples we use:**
- "Act as a security expert auditing this authentication code"
- "Act as a DevOps engineer reviewing our deployment strategy"
- "Act as a technical writer documenting this API for mobile developers"
- "Act as a CodeIgniter 4 core contributor reviewing this implementation"

Each role triggers different knowledge and priorities. A "security expert" will flag vulnerabilities that a "developer" might overlook. A "technical writer" will suggest clearer error messages. The role shapes the response.

#### C - Clarify the Context

This is where you tell the AI about your specific situation. Remember, the AI doesn't know you're using CodeIgniter 4, Shield for authentication, and MySQL for your database—unless you tell it.

**Instead of:** "I need to protect this route"

**Say:** "I'm working on a CodeIgniter 4 project using Shield for authentication. The project structure follows CI4 conventions with controllers in app/Controllers/Api/, models in app/Models/, and routes defined in app/Config/Routes.php. I need to protect an API endpoint so only authenticated users with valid bearer tokens can access it."

Now the AI knows:
- The framework (CodeIgniter 4)
- The auth library (Shield)
- The directory structure
- The specific protection mechanism (bearer tokens)

It can give you exact code that fits your project instead of generic middleware examples from Laravel or Express.js.

**Key context to always include:**
- Your tech stack (framework, libraries, database)
- Your project structure (where files live)
- Your authentication method (session, token, JWT, etc.)
- What you've already tried (if debugging)
- The specific file or code you're working with

#### T - Specify the Task

Be crystal clear about what you want the AI to do. Vague requests get vague answers.

**Instead of:** "Make this better"

**Say:** "Review this controller method and:
1. Identify any security vulnerabilities
2. Suggest input validation improvements
3. Recommend better error handling
4. Show me the improved code with comments explaining each change"

Now the AI has a checklist. It knows exactly what "better" means in this context.

**Task specification tips:**
- Use action verbs: "Review," "Refactor," "Explain," "Compare," "Implement"
- Be specific about deliverables: "code," "explanation," "pros/cons list"
- Set boundaries: "Keep it simple" or "Prioritize security over brevity"
- Ask for multiple options: "Give me two approaches and explain when to use each"

#### S - Set the Standards

This is where you define what "good" looks like for your project. Different teams have different priorities—some care about performance, others about readability, others about security above all else.

**Instead of:** "Write this code"

**Say:** "Write this code following these standards:
- Prioritize security and input validation over code brevity
- Follow CodeIgniter 4 conventions and coding style
- Include comprehensive PHPDoc comments explaining parameters and return values
- Handle all error cases gracefully with appropriate HTTP status codes
- Use type hints where appropriate for PHP 8.2+
- Don't use external libraries unless absolutely necessary"

Now the AI knows your values. It won't give you clever one-liners that are impossible to maintain. It won't skip error handling to make the code shorter. It understands your definition of quality.

**Standards we commonly set:**
- "Security is more important than convenience"
- "Explain your reasoning for each significant decision"
- "Write code that a junior developer could understand"
- "Consider edge cases and validation"
- "Follow the existing patterns in our codebase"

### Real Examples from Our Project

Let me show you actual prompts we used while building LaunchPad API. These aren't theoretical—they're copied straight from our chat history (with sensitive info removed).

#### Example 1: Creating a New Endpoint

**Our prompt:**
```
Act as a senior CodeIgniter 4 developer specializing in REST API design.

Context:
- We're building LaunchPad API using CodeIgniter 4.5.x with Shield authentication
- Our API controllers are in app/Controllers/Api/ and extend ResourceController
- We're using MySQL with CI4's Query Builder
- The project follows PSR-4 autoloading and CI4 conventions

Task:
Create a controller method that handles GET requests to retrieve a paginated list of users. The endpoint should:
1. Require authentication (bearer tokens via Shield)
2. Support pagination parameters (page, per_page)
3. Allow optional filtering by user status (active, inactive)
4. Return a JSON response with proper HTTP status codes
5. Include metadata about total records and pagination

Standards:
- Use ResourceController's built-in methods where appropriate
- Validate all input parameters
- Handle database errors gracefully
- Include PHPDoc comments
- Follow CI4's ResponseTrait patterns for consistency
- Security is the top priority—assume all input is malicious
```

**What we got back:**
The AI gave us a complete, production-ready method with input validation, error handling, proper pagination using CI4's built-in features, and security considerations. It explained why certain choices were made (like using Query Builder to prevent SQL injection). It took 10 seconds instead of the 30 minutes it would have taken us to write and test.

#### Example 2: Debugging an Authentication Issue

**Our prompt:**
```
Act as a CodeIgniter 4 security expert debugging an authentication problem.

Context:
- CI4 project with Shield authentication
- We're using API tokens (not sessions)
- The TokenAuth filter is applied to our API routes
- Users can generate tokens via /api/auth/login successfully
- Tokens are stored in the auth_identities table

The Problem:
When we make requests to protected endpoints with a valid token in the Authorization header (Bearer TOKEN), we get a 401 Unauthorized response. The token definitely exists in the database and isn't expired.

What we've checked:
- The Authorization header is being sent correctly (verified with Postman)
- The token exists in auth_identities with type 'access_token'
- The token's expires_at is null (shouldn't expire)
- The filter is definitely being applied (we see it in the route config)

Task:
1. List the most likely causes of this issue in order of probability
2. For each cause, explain how to verify if it's the problem
3. Provide the specific code/config changes needed to fix it
4. Explain why this is happening so we can prevent it in the future
```

**What we got back:**
The AI walked us through a systematic debugging process. It turned out we had forgotten to enable the "token" authenticator in Shield's config (only "session" was enabled). The AI explained that Shield needs explicit configuration for which auth methods to use, gave us the exact config file to edit, and explained the difference between session and token authentication so we understood why this mattered.

This response saved us probably 2 hours of random trial-and-error debugging.

#### Example 3: Reviewing Security

**Our prompt:**
```
Act as a security auditor reviewing our API authentication implementation.

Context:
We're building a production API that will handle sensitive user data. We've implemented Shield authentication with the following setup:
[we pasted our configuration and key controller methods here]

Task:
Perform a security audit and tell us:
1. What we're doing well (security strengths)
2. What vulnerabilities exist or could exist
3. What industry best practices we're missing
4. Specific recommendations with code examples for any fixes needed
5. How to test that our security is working correctly

Standards:
- Be thorough—assume this will be attacked by sophisticated actors
- Prioritize OWASP Top 10 considerations
- Consider both technical vulnerabilities and logic flaws
- Explain the "why" behind each recommendation, not just the "what"
```

**What we got back:**
The AI identified three issues we hadn't considered:
1. We weren't rate-limiting our login endpoint (vulnerable to brute force)
2. Our error messages were too specific, potentially leaking information about which users exist
3. We weren't validating the strength of passwords during registration

For each issue, it explained the attack vector, showed us exactly how to fix it with code, and explained why it mattered. This level of security review would have cost hundreds of dollars from a consultant. We got it in 60 seconds.

### The Prompts We Use Over and Over

After building LaunchPad API, we noticed we were using certain prompt patterns repeatedly. Here are our "go-to" templates:

**For generating new code:**
```
Act as a [role] with expertise in [specific technology].

Context:
- [Brief project description]
- [Tech stack details]
- [Relevant file locations]
- [Any relevant configuration]

Task:
[Specific, actionable task with numbered requirements if complex]

Standards:
- [Priority 1: usually security or performance]
- [Code style requirements]
- [Documentation requirements]
- [Error handling expectations]
```

**For debugging:**
```
Act as an expert debugger specializing in [technology].

Context:
- [What you're building]
- [What's supposed to happen]
- [What's actually happening]
- [Error messages or unexpected behavior]

What I've already tried:
1. [First thing you checked]
2. [Second thing you checked]
3. [Any relevant tests you ran]

Task:
1. Identify the most likely root causes
2. Explain how to verify each one
3. Provide the fix with code
4. Explain why this happened to prevent it in the future
```

**For explaining concepts:**
```
Act as a patient technical mentor explaining [concept] to a [experience level] developer.

Context:
I'm working on [brief description] and trying to understand [specific concept]. I've read [what you've already read] but I'm still unclear on [specific confusion].

Task:
Explain [concept] in simple terms using:
- An analogy from everyday life
- A simple code example
- The specific way it applies to my situation
- Common mistakes to avoid

Standards:
- Assume I'm smart but new to this specific area
- Don't use jargon without explaining it
- Connect it to practical benefits (why should I care?)
```

**For comparing options:**
```
Act as a senior architect helping choose between technical approaches.

Context:
We're deciding between [Option A] and [Option B] for [specific use case].

Current situation:
- [Brief project context]
- [Any constraints or requirements]
- [Team experience level]
- [Performance/security needs]

Task:
Compare these approaches across these dimensions:
1. Security implications
2. Performance characteristics
3. Maintainability and readability
4. Learning curve for the team
5. Long-term scalability

For each option, provide:
- Clear pros and cons
- When to choose this option
- A brief code example showing the implementation
- Any gotchas or common pitfalls

Standards:
- Be objective—don't favor one just because it's newer or cooler
- Consider our context (we're [team situation])
- Flag any irreversible decisions
```

### Why This Matters More Than You Think

You might be thinking, "This seems like a lot of work just to ask a question." And at first, it does feel that way. Writing a detailed prompt takes 2-3 minutes instead of 10 seconds.

But here's what we learned: **A good prompt saves hours.**

When you write a vague prompt, you get a vague answer. Then you spend 20 minutes trying to implement it, only to realize it doesn't fit your situation. So you go back, clarify, try again. Three cycles later, you've spent an hour.

Or worse, you get code that seems to work but has hidden issues—security holes, performance problems, bad practices. You don't find out until weeks later when something breaks or a user exploits a vulnerability.

A detailed prompt takes 3 minutes to write but gives you exactly what you need the first time. It considers your constraints, follows your standards, and fits your project. You implement it once and it works.

**The math is simple:** 3 minutes of good prompting vs. 60+ minutes of back-and-forth and debugging. Plus the peace of mind knowing you got a secure, high-quality solution.

### Common Mistakes We Made (So You Don't Have To)

Let me share the mistakes we made while learning this. Maybe you'll recognize some of these:

**Mistake 1: Being too brief**
- What we did: "Fix this"
- What happened: The AI made assumptions, changed things we didn't want changed, and introduced new issues
- The fix: Always explain what "fix" means and provide context

**Mistake 2: Not specifying the role**
- What we did: Asked general programming questions without assigning expertise
- What happened: Got generic answers that missed framework-specific best practices
- The fix: Always start with "Act as a [specific expert in specific technology]"

**Mistake 3: Not setting priorities**
- What we did: "Make this code better"
- What happened: The AI optimized for brevity and created unreadable one-liners
- What we wanted: Security and maintainability over cleverness
- The fix: Explicitly state your priorities

**Mistake 4: Asking for code without explanation**
- What we did: "Give me the code for X"
- What happened: Got working code but didn't understand it, couldn't modify it, couldn't debug it
- The fix: Always ask "explain how this works" or "add comments explaining each part"

**Mistake 5: Not providing file context**
- What we did: Pasted a code snippet without saying which file it was from
- What happened: The AI suggested imports and namespaces that didn't match our structure
- The fix: Always mention the file path and project structure

**Mistake 6: Being afraid to ask "dumb" questions**
- What we did: Struggled with concepts we didn't understand instead of asking for clarification
- What happened: Built features on shaky foundations, created technical debt
- The fix: Use the "patient mentor" role and ask for explanations in simple terms. No judgment, just learning.

### The Mindset Shift: AI as a Collaborative Partner

Here's the philosophical shift that made all the difference for us:

**Old mindset:** "AI is a tool I use to get answers"
**New mindset:** "AI is a collaborative partner who needs context to be helpful"

When you view AI as a partner, you naturally provide more context. You explain your goals, constraints, and reasoning. You have a dialogue instead of making demands.

Think about how you'd work with a human developer:
- You wouldn't just say "fix this" and walk away
- You'd explain what's wrong, what you've tried, and what success looks like
- You'd share your project structure and standards
- You'd listen to their questions and provide clarification

Treat AI the same way. The prompts that work best are the ones that treat AI like a knowledgeable colleague who just joined your project and needs to get up to speed.

### Our Prompt Engineering Checklist

Before sending any prompt to our AI assistant, we now run through this mental checklist:

**Role Assignment:**
- [ ] Did I specify what expertise the AI should use?
- [ ] Is the role specific to my technology stack?
- [ ] Does the role match the type of help I need (developer vs. security expert vs. architect)?

**Context Provided:**
- [ ] Did I mention the framework and libraries I'm using?
- [ ] Did I describe my project structure?
- [ ] Did I include relevant code or configuration?
- [ ] If debugging, did I say what I've already tried?

**Task Clarity:**
- [ ] Is the task specific and actionable?
- [ ] Did I break complex tasks into numbered steps?
- [ ] Did I specify what deliverables I want (code, explanation, comparison)?

**Standards Set:**
- [ ] Did I state my priorities (security, performance, readability)?
- [ ] Did I mention any constraints or requirements?
- [ ] Did I specify coding style or documentation expectations?

**Tone Check:**
- [ ] Am I treating AI like a collaborative partner?
- [ ] Did I provide enough detail for the AI to understand my situation?
- [ ] Would a human developer understand what I'm asking for?

If we can check all these boxes, we get great results almost every time.

### Putting It All Together: A Complete Example

Let me show you one final, comprehensive example that demonstrates everything we've learned.

**The Situation:**
We needed to implement a password reset feature. This is security-critical, so we wanted to be extra careful.

**Our Prompt:**
```
Act as a senior CodeIgniter 4 security expert with deep knowledge of Shield authentication and modern security best practices.

Context:
We're building LaunchPad API, a production REST API using:
- CodeIgniter 4.5.x
- Shield for authentication (currently using tokens)
- MySQL database
- PHP 8.2+
- Following CI4 conventions and PSR standards

Our project structure:
- Controllers: app/Controllers/Api/
- Models: app/Models/
- Config: app/Config/
- Routes: app/Config/Routes.php

Current authentication setup:
[We pasted our Shield configuration here]

The Task:
Implement a secure password reset flow for our API that:
1. Allows users to request a password reset via their email
2. Generates a secure, time-limited token
3. Sends an email with a reset link
4. Validates the token when user clicks the link
5. Allows setting a new password with validation
6. Invalidates the token after use or expiration

Security Requirements (in priority order):
1. Prevent timing attacks (don't reveal if email exists)
2. Tokens must be cryptographically secure and time-limited
3. Prevent replay attacks (token can only be used once)
4. Validate new password strength
5. Log all password reset attempts for security monitoring
6. Rate limit reset requests to prevent abuse

Code Standards:
- Use Shield's built-in features where possible
- Follow CI4's validation and response patterns
- Include comprehensive PHPDoc comments
- Handle all error cases gracefully
- Use type hints for PHP 8.2+
- Assume all input is malicious

Deliverables:
1. The controller method(s) for handling reset requests
2. Any model changes needed
3. Route configuration
4. Shield configuration updates
5. A brief explanation of the security measures implemented
6. Testing suggestions to verify the security
```

**The Result:**
The AI gave us a complete, production-ready implementation with:
- Secure token generation using CI4's security features
- Timing-attack-resistant email lookup
- Proper token expiration handling
- Rate limiting implementation
- Comprehensive validation
- Clear error messages that don't leak information
- Detailed comments explaining each security decision

It took us 5 minutes to review and adapt to our exact needs. Without good prompting, we might have gotten a basic implementation that "worked" but had security holes we'd discover months later when someone exploited them.

### The Bottom Line on Prompt Engineering

Prompt engineering isn't about manipulating AI or using special keywords. It's about clear communication—the same skill you use when working with human colleagues.

The best prompts:
- Set clear expectations (role assignment)
- Provide necessary context (clarify the situation)
- Define specific goals (specify the task)
- Establish quality standards (set the bar)

When you get a bad response from AI, it's usually not because the AI is bad—it's because the prompt was incomplete. The AI gave you exactly what you asked for; you just didn't ask for the right thing.

**Our advice:** Spend 3 minutes writing a detailed prompt, save 3 hours of debugging. Treat AI like the knowledgeable partner it is, give it the context it needs, and you'll be amazed at the quality of help you receive.

This is the final piece of the Vibe Coding methodology. With good documentation, trained AI skills, proper libraries, and effective prompting, you have everything you need to build production software at a pace that would seem impossible to traditional developers.

Now let's talk about how we document everything so our future selves (and our AI assistants) can understand the reasoning behind every decision.

## The AGENTS.md Philosophy: Documenting Everything

There's a file in our project called `AGENTS.md` that's worth talking about because it represents a fundamental shift in how we think about software development.

### Why We Document Decisions

Most code has comments explaining WHAT it does. Rarely does it explain WHY it does it that way. Six months later, you'll look at your code and think "Why did I do it this way? Was there a reason?"

Or worse, a new developer joins your team and has to reverse-engineer your decisions by reading code and guessing.

**Our rule: Every technical decision gets documented.**

When we chose CodeIgniter over Laravel: documented.
When we chose Shield for authentication: documented.
When we structured our folders a certain way: documented.
When we configured security settings: documented.

### What's in AGENTS.md?

Our AGENTS.md file has become the living brain of our project:

**1. Project Overview**
- What we're building
- Our tech stack
- Directory structure

**2. Common Commands**
- How to start the development server
- How to run database migrations
- How to create new controllers or models
- How to run tests

**3. Development Standards**
- How we structure controllers
- How we structure models
- Security checklist
- Code style guidelines

**4. Configuration Reference**
- What each config file does
- Which settings we've changed
- Why we changed them

**5. Available Skills**
- Links to all our skill files
- What each one covers
- When to reference which one

**6. Key Documentation**
- Links to our local documentation
- Which files cover which topics
- Where to find deeper information

**7. Troubleshooting**
- Common problems we've hit
- How we solved them
- What to check when things break

**8. Best Practices**
- Security principles we follow
- Performance tips
- Testing requirements

### The Decision-Making Format

When we document a decision, we use this format:

```markdown
## Decision: [What we decided]

**Date**: [When we decided it]
**Context**: [What situation led to this decision]
**Options Considered**:
- Option A: [description]
- Option B: [description]
- Option C: [description]

**Decision**: We chose Option B because [specific reasons]

**Trade-offs**:
- Pros: [benefits]
- Cons: [drawbacks]

**Reversible?**: [Yes/No] - If yes, under what conditions?
```

**Real Example from Our Project:**

```markdown
## Decision: Use Shield for Authentication

**Date**: February 17, 2026
**Context**: We need user authentication for LaunchPad API

**Options Considered**:
1. Write our own authentication system
2. Use Shield (CodeIgniter's official auth library)
3. Use a third-party service (Auth0, Firebase Auth)

**Decision**: We chose Shield because:
- It's the official CodeIgniter authentication solution
- It integrates seamlessly with our framework
- It supports multiple auth methods (sessions, tokens, HMAC, JWT)
- It has role-based permissions built-in
- It's actively maintained by the CodeIgniter team
- It doesn't lock us into a third-party service

**Trade-offs**:
- Pros: Free, integrated, full control, no vendor lock-in
- Cons: We maintain it ourselves (but this is minimal with Composer updates)

**Reversible?**: Partially. If we want to switch to a third-party service later, we can migrate users. But Shield gives us everything we need for the foreseeable future.
```

### Why This Matters for AI

Here's the beautiful thing: **Our AI assistant reads AGENTS.md.**

When we ask OpenCode for help, it knows:
- Our project structure
- Our coding standards
- Our security requirements
- Where to find documentation
- What decisions we've already made

This means the AI gives us consistent advice that matches our project's philosophy. It doesn't suggest solutions that conflict with our established patterns. It understands the constraints and goals we've set.

It's like the difference between asking a stranger for directions versus asking someone who's read your entire project plan.

## Code Examples: What We Actually Built

Let's look at some real code from LaunchPad API. Remember, you don't need to memorize this—you just need to see that it's manageable.

### Example 1: A Simple Protected Endpoint

This gets a user's profile, but only if they're logged in:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class ProfileController extends ResourceController
{
    protected $format = 'json';

    /**
     * Get the current user's profile
     * GET /api/profile
     */
    public function index()
    {
        // auth() is a helper function from Shield
        // It gives us access to the current user
        $user = auth()->user();
        
        // If somehow no user is logged in, return error
        if (!$user) {
            return $this->failUnauthorized('You must be logged in');
        }
        
        // Return the user data
        return $this->respond([
            'status' => 200,
            'data' => [
                'id' => $user->id,
                'email' => $user->email,
                'username' => $user->username,
                'created_at' => $user->created_at
            ]
        ]);
    }
}
```

**What's happening here:**
- We extend ResourceController which gives us helpful methods
- `auth()->user()` gets the currently logged-in user from their token
- If no user, we return a 401 Unauthorized error
- If yes, we return their profile data

**To protect this route in routes.php:**

```php
$routes->get('api/profile', 'Api\ProfileController::index', ['filter' => 'tokens']);
```

That's it. One line says "require a valid token to access this."

### Example 2: Creating a New Resource (with Validation)

This creates a new product in our database:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class ProductController extends ResourceController
{
    protected $modelName = 'App\Models\ProductModel';
    protected $format = 'json';

    /**
     * Create a new product
     * POST /api/products
     */
    public function create()
    {
        // Get the JSON data sent by the client
        $data = $this->request->getJSON(true);
        
        // Try to insert into database
        // The model validates automatically based on rules we defined
        if (!$this->model->insert($data)) {
            // Validation failed - return the errors
            return $this->failValidationErrors($this->model->errors());
        }
        
        // Success! Return the new product ID
        return $this->respondCreated([
            'id' => $this->model->insertID(),
            'message' => 'Product created successfully'
        ]);
    }
}
```

**What's happening here:**
- `getJSON(true)` parses the JSON sent by the client into a PHP array
- `$this->model->insert($data)` tries to save to database
- If validation fails (wrong data types, missing fields), we get errors back
- `respondCreated()` automatically sends HTTP 201 (Created) status

**The model with validation rules:**

```php
<?php

namespace App\Models;

use CodeIgniter\Model;

class ProductModel extends Model
{
    protected $table = 'products';
    protected $primaryKey = 'id';
    
    // Fields that can be mass-assigned
    protected $allowedFields = ['name', 'description', 'price', 'stock'];
    
    // Validation rules
    protected $validationRules = [
        'name' => 'required|min_length[3]|max_length[255]',
        'description' => 'permit_empty|max_length[1000]',
        'price' => 'required|decimal|greater_than[0]',
        'stock' => 'required|integer|greater_than_equal_to[0]'
    ];
    
    // Custom error messages
    protected $validationMessages = [
        'name' => [
            'required' => 'Product name is required',
            'min_length' => 'Product name must be at least 3 characters'
        ],
        'price' => [
            'required' => 'Price is required',
            'greater_than' => 'Price must be greater than 0'
        ]
    ];
}
```

Notice how the model handles all validation? We don't write validation logic in our controller—we define the rules once, and the model enforces them automatically.

### Example 3: Checking Permissions

Sometimes we need to check if a user has specific permission, not just if they're logged in:

```php
<?php

namespace App\Controllers\Api;

use CodeIgniter\RESTful\ResourceController;

class AdminController extends ResourceController
{
    protected $format = 'json';

    /**
     * Get all users (admin only)
     * GET /api/admin/users
     */
    public function users()
    {
        $user = auth()->user();
        
        // Check if user has admin permission
        if (!$user->can('admin.access')) {
            return $this->failForbidden('You do not have permission to access this area');
        }
        
        // Load user model
        $userModel = model('UserModel');
        
        // Get all users
        $users = $userModel->findAll();
        
        return $this->respond([
            'status' => 200,
            'count' => count($users),
            'data' => $users
        ]);
    }
}
```

**What's happening:**
- `auth()->user()` gets current user
- `$user->can('admin.access')` checks if they have the admin permission
- If not, return 403 Forbidden
- If yes, show all users

**Setting up permissions in AuthGroups.php:**

```php
<?php

namespace Config;

use CodeIgniter\Shield\Config\AuthGroups as ShieldAuthGroups;

class AuthGroups extends ShieldAuthGroups
{
    // Define user groups
    public array $groups = [
        'superadmin' => [
            'title' => 'Super Admin',
            'description' => 'Complete system access'
        ],
        'admin' => [
            'title' => 'Administrator', 
            'description' => 'Day-to-day administrators'
        ],
        'user' => [
            'title' => 'User',
            'description' => 'General users'
        ]
    ];

    // Define permissions
    public array $permissions = [
        'admin.access' => 'Can access admin area',
        'users.create' => 'Can create users',
        'users.edit' => 'Can edit users',
        'users.delete' => 'Can delete users',
        'products.manage' => 'Can manage products'
    ];

    // Which groups have which permissions
    public array $matrix = [
        'superadmin' => ['*'],  // Wildcard = all permissions
        'admin' => [
            'admin.access',
            'users.*',  // All user permissions
            'products.manage'
        ],
        'user' => [
            'products.read'  // Can only view products
        ]
    ];
}
```

This creates a complete role-based access control system. Users in the "admin" group automatically get all the permissions listed, and we can check `$user->can('users.create')` anywhere in our code.

## Leveraging OpenCode AI: Our Day-to-Day Workflow

Now that you understand what we built, let's talk about HOW we built it. This is where Vibe Coding really shines.

### Our Daily Workflow

**Morning Setup (5 minutes):**
1. Open our code editor with OpenCode integrated
2. Open the project folder
3. Ask OpenCode: "What's our goal for today?"
4. Review yesterday's progress

**Building Features (The Vibe):**

Let's walk through adding a real feature: "User profile update endpoint"

**Step 1: Ask for the plan**

Us: "We need to add an endpoint that lets users update their profile. They should be able to update their name, email, and bio. What files do we need to create or modify?"

OpenCode: "Based on our project structure and the ci4-api-development skill, we'll need to:

1. Add an `update()` method to `ProfileController`
2. Update validation rules in the User model to allow bio field
3. Add a route in `Routes.php`
4. Consider: Should users be able to change their email? That might require re-verification.

Let me show you the controller method first."

**Step 2: Get the code**

OpenCode generates:

```php
public function update()
{
    $user = auth()->user();
    
    if (!$user) {
        return $this->failUnauthorized('You must be logged in');
    }
    
    $data = $this->request->getJSON(true);
    
    // Only allow certain fields to be updated
    $allowedFields = ['username', 'bio'];
    $updateData = array_intersect_key($data, array_flip($allowedFields));
    
    // Handle email separately (requires verification)
    if (isset($data['email']) && $data['email'] !== $user->email) {
        // Trigger email change process
        return $this->failValidationErrors([
            'email' => 'Email changes require verification. Use the email change endpoint.'
        ]);
    }
    
    if (empty($updateData)) {
        return $this->failValidationErrors(['error' => 'No valid fields to update']);
    }
    
    $userModel = model('UserModel');
    
    if (!$userModel->update($user->id, $updateData)) {
        return $this->failValidationErrors($userModel->errors());
    }
    
    return $this->respondUpdated([
        'message' => 'Profile updated successfully',
        'data' => $userModel->find($user->id)
    ]);
}
```

**Step 3: Ask questions**

Us: "Why are we using `array_intersect_key`?"

OpenCode: "Great question! This is a security measure. It ensures we only update fields we explicitly allow. Without this, a malicious user could send extra fields in their JSON (like `is_admin: true`) and potentially escalate their privileges. We whitelist allowed fields instead of blacklisting dangerous ones—it's safer."

Us: "Ah, that makes sense. What about the email verification?"

OpenCode: "Email is special because it's often used for account recovery and is a unique identifier. If we let users change it instantly, someone could:
1. Take over an account by changing to an email they control
2. Lock out the real owner
3. Bypass security measures

The better flow is:
1. User requests email change
2. System sends verification to NEW email
3. User clicks link in new email
4. System updates email only after verification

Shield might have built-in email change handling we can use. Check the ci4-shield-auth skill file."

**Step 4: Implement and test**

We add the code, update the route:

```php
$routes->put('api/profile', 'Api\ProfileController::update', ['filter' => 'tokens']);
```

Then we test it:

```bash
# Start the development server
php spark serve

# In another terminal, test with curl
curl -X PUT http://localhost:8080/api/profile \
  -H "Authorization: Bearer YOUR_TOKEN_HERE" \
  -H "Content-Type: application/json" \
  -d '{"username": "NewName", "bio": "Hello world"}'
```

**Step 5: Handle errors**

If something doesn't work, we ask OpenCode:

Us: "I'm getting a 500 error when I try to update. The logs say 'Unknown column bio in field list.'"

OpenCode: "That means the database table doesn't have a 'bio' column yet. We need to create a migration to add it. Let me create that for you."

```bash
# Generate migration
php spark make:migration add_bio_to_users_table
```

OpenCode generates the migration code:

```php
<?php

namespace App\Database\Migrations;

use CodeIgniter\Database\Migration;

class AddBioToUsersTable extends Migration
{
    public function up()
    {
        $this->forge->addColumn('users', [
            'bio' => [
                'type' => 'TEXT',
                'null' => true,
                'after' => 'username'
            ]
        ]);
    }

    public function down()
    {
        $this->forge->dropColumn('users', 'bio');
    }
}
```

Then:

```bash
# Run the migration
php spark migrate
```

Problem solved.

### The Key Insight

Notice how this isn't just "AI writes code for us." It's a conversation:
- We explain what we want
- AI suggests an approach and explains why
- We ask questions
- AI teaches us the reasoning
- We implement
- We test
- We fix issues together

We're learning while building. By the time this feature is done, we understand:
- Mass assignment vulnerabilities
- Why email changes need verification
- How migrations work
- How to test API endpoints

That's the "Vibe" in Vibe Coding. It's collaborative, educational, and productive.

## Technical Decisions: The Why Behind What We Built

Let's document some key decisions we made during this project, using our decision format:

### Decision: Store Documentation Locally vs. Rely on Online Docs

**Date**: February 17, 2026
**Context**: We need the AI to give us accurate, current advice about CodeIgniter and Shield

**Options Considered**:
1. Point AI to online documentation (codeigniter.com)
2. Download documentation locally and point AI to that
3. Don't use documentation, rely on AI's training data

**Decision**: We chose option 2—download locally

**Rationale**:
- Online docs might be temporarily down
- AI's training data might be outdated (pre-CodeIgniter 4 or older versions)
- Local docs allow offline development
- We can search local docs instantly
- It ensures the AI references the exact same version we're using

**Trade-offs**:
- Pros: Reliable, version-specific, searchable offline
- Cons: Takes up disk space (~50MB), need to update periodically

**Reversible?**: Yes. If we want to use online docs later, we just update the skill files.

### Decision: Use CodeIgniter 4 Over Laravel or Other Frameworks

**Date**: February 17, 2026
**Context**: Choosing a PHP framework for our API

**Options Considered**:
1. Laravel (most popular PHP framework)
2. CodeIgniter 4 (lightweight, simple)
3. Symfony (enterprise-focused)
4. Slim (micro-framework)
5. No framework (pure PHP)

**Decision**: CodeIgniter 4

**Rationale**:
- **Laravel**: Powerful but opinionated and complex. Has a steep learning curve. Heavy for a simple API.
- **CodeIgniter**: Simple, clear documentation, gets out of your way. Perfect for learning while building.
- **Symfony**: Overkill for our needs. Designed for large enterprise apps.
- **Slim**: Too minimal. We'd end up rebuilding features CI4 provides.
- **Pure PHP**: We'd reinvent the wheel and introduce security issues.

CI4 hits the sweet spot: opinionated enough to guide us, flexible enough to not fight us.

**Trade-offs**:
- Pros: Fast to learn, excellent documentation, built-in API features
- Cons: Smaller ecosystem than Laravel, fewer third-party packages

**Reversible?**: Technically yes, but practically no. Rewriting in another framework would be a complete rebuild.

### Decision: Use Shield's Token Authentication vs. JWT

**Date**: February 17, 2026
**Context**: Choosing authentication method for API

**Options Considered**:
1. Shield's built-in Access Tokens
2. JWT (JSON Web Tokens)
3. Session-based auth (cookies)
4. OAuth2 (Google, GitHub login)

**Decision**: Shield's Access Tokens for now, with option to add JWT later

**Rationale**:
- **Access Tokens**: Built into Shield, no extra dependencies, stored in database (we can revoke them instantly), simple to implement
- **JWT**: Popular, self-contained, but requires additional package (shield-jwt), harder to revoke (need blacklist), larger token size
- **Sessions**: Not suitable for API (designed for browser-based web apps)
- **OAuth2**: Good for "Login with Google" but adds complexity and external dependency

Access tokens give us everything we need for a basic API: stateless authentication, expiration, scopes, and the ability to revoke. We can add JWT later if we need its specific benefits.

**Trade-offs**:
- Pros: Simple, secure, instantly revocable, no extra dependencies
- Cons: Requires database lookup on each request (minimal performance impact)

**Reversible?**: Yes. We can add JWT support alongside access tokens if needed.

### Decision: Use MySQL vs. PostgreSQL or SQLite

**Date**: February 17, 2026
**Context**: Choosing database for development and production

**Options Considered**:
1. MySQL (most popular, widely supported)
2. PostgreSQL (more advanced features)
3. SQLite (file-based, zero setup)

**Decision**: MySQL for production, SQLite for development/testing

**Rationale**:
- **MySQL**: Every shared host supports it. Massive community. Perfect for our needs.
- **PostgreSQL**: Better in some ways, but not supported by most shared hosting. Adds deployment complexity.
- **SQLite**: Great for development (no server to run), not suitable for production (concurrency issues)

We'll develop with SQLite (fast, easy) and deploy to MySQL (universal support).

**Trade-offs**:
- Pros: Universal hosting support, easy to find help, simple deployment
- Cons: Less advanced than PostgreSQL (but we don't need those features)

**Reversible?**: Partially. CodeIgniter makes switching databases relatively easy, but data migration would be required.

### Decision: Skill-Based Organization vs. Monolithic Documentation

**Date**: February 17, 2026
**Context**: How to structure AI knowledge for the project

**Options Considered**:
1. One giant skills file with everything
2. Multiple focused skill files by topic
3. No skills, just rely on AGENTS.md

**Decision**: Multiple focused skill files

**Rationale**:
- **One giant file**: Hard to navigate, AI might miss relevant context
- **Multiple files**: Clear organization, can reference specific areas, easier to maintain
- **No skills**: AI would give generic advice, not optimized for our stack

We created 7 skill files covering distinct areas. When we need help with authentication, we (and the AI) know to reference ci4-shield-auth.

**Trade-offs**:
- Pros: Organized, maintainable, focused context
- Cons: Need to know which skill to reference (but that's easy to learn)

**Reversible?**: Yes. We can merge or split skill files anytime.

## Common Concerns Addressed

### "But I'm Not Technical Enough!"

We hear this a lot. Here's our perspective:

**You don't need to be a computer scientist. You need to be persistent.**

Think about learning to drive:
- You didn't need to understand internal combustion engines
- You didn't need to be a mechanic
- You learned the controls, practiced, and gradually got comfortable
- Now you drive without thinking about it

Coding is similar. You learn:
- The basic syntax (like learning the controls)
- Common patterns (like learning traffic rules)
- How to read errors (like learning dashboard warnings)
- Where to find help (like knowing you can Google or ask a mechanic)

The AI handles the complex syntax. You focus on the logic: "When a user does X, the system should do Y." That's not a technical skill—that's understanding your business.

### "What If I Break Something?"

**Three words: Version Control (Git).**

We use Git to track every change. Think of it like an infinite undo button that remembers everything.

Before we make any significant change:
1. We save our current state (commit)
2. We make the change
3. If it works: great!
4. If it breaks: we restore the previous state (revert)

It's like saving a video game before a boss fight. If you lose, you reload. No progress lost.

Plus:
- Breaking things is how you learn
- Local development means you can't break the production site
- Tests catch problems before users see them
- The AI helps fix errors

### "Will This Actually Scale?"

We addressed this earlier, but let's be specific:

**LaunchPad API can handle:**
- Thousands of users
- Hundreds of requests per second (on modest hardware)
- Millions of database records (with proper indexing)

**If you grow beyond that:**
- Add caching (Redis)
- Add a CDN for static files
- Upgrade to a VPS ($20/month handles much more traffic)
- Add load balancing
- Optimize database queries

But here's the key: **You don't optimize for millions of users when you have zero users.**

Build for your current needs. When you have traction and revenue, you can afford to optimize. Premature optimization is spending time and money on problems you don't have yet.

### "What If I Need to Hire Developers Later?"

This is actually a strength of our approach:

**Good news:**
- PHP developers are everywhere (it's the most popular web language)
- CodeIgniter developers are easy to find
- Our code follows best practices
- AGENTS.md explains every decision
- Skill files show how we work

A new developer can:
1. Read AGENTS.md to understand the project
2. Read the skill files to understand our stack
3. Look at existing code to see our patterns
4. Ask the AI for help (it's trained on our docs)

They'll be productive in days, not weeks.

### "Isn't This Cheating?"

**No. It's leveraging tools.**

Did calculators "cheat" mathematics? No, they made us more productive.

Does a carpenter "cheat" by using power tools instead of hand saws? No, they work smarter.

AI is just a tool. The value you provide is:
- Understanding the problem you're solving
- Designing the solution
- Making decisions about architecture and trade-offs
- Testing that it works for real users
- Iterating based on feedback

The AI helps with syntax and boilerplate. You provide the vision and judgment.

## The Real Costs and Time Investment

Let's be honest about what this actually takes:

### Traditional Path (Hiring a Developer)

**Timeline:** 4-8 weeks
**Cost:** $5,000-$30,000
**What you get:** Working API (hopefully)
**What you don't get:** Understanding of how it works, ability to make changes yourself

**Ongoing:**
- Every change costs more money
- Dependency on their availability
- Risk if they disappear
- Communication overhead

### Vibe Coding Path (What We Did)

**Learning Phase:** 1-2 weeks
- Setting up environment: 1 day
- Understanding basics: 3-5 days
- Working with AI effectively: 3-5 days

**Building Phase:** 1-2 weeks
- Setting up framework: 1 day
- Implementing authentication: 2-3 days
- Building your specific features: 5-10 days

**Cost:**
- AI assistant: $0-20/month (OpenCode is free, alternatives vary)
- Hosting: $3-10/month
- Your time: But you're learning valuable skills

**What you get:**
- Working API
- Deep understanding of how it works
- Ability to make any changes yourself
- Reusable skills for future projects
- Documentation of every decision

**Ongoing:**
- You can iterate instantly
- No dependency on others
- Every change makes you better
- New features take hours, not days

### The Hidden Benefits

1. **Speed of Iteration**: When a customer requests a feature, you can ship it the same day
2. **Learning Compound Interest**: Each project gets faster. Your second API will take half the time
3. **Technical Confidence**: You can evaluate contractors and understand what they're doing
4. **Pivot Ability**: If your business needs change, you can adapt your tech instantly
5. **Ownership**: You own your intellectual property completely

## What We Have Now: LaunchPad API Features

Let's summarize what's actually built and working:

### ✅ Authentication System
- User registration with email validation
- Secure login with password hashing (Argon2id)
- Password reset via secure tokens
- Session management
- API access tokens with expiration
- Token scopes (read, write, admin)
- Rate limiting on auth endpoints (prevents brute force)

### ✅ Authorization System
- User groups (admin, user, etc.)
- Granular permissions
- Group-based permission matrix
- Easy permission checking in code

### ✅ API Foundation
- RESTful endpoint structure
- Consistent JSON responses
- Proper HTTP status codes
- Error handling
- Input validation
- Content negotiation (JSON/XML)

### ✅ Database System
- Migration system (version-controlled schema changes)
- Seeders (test data)
- Query builder (secure database access)
- Model relationships

### ✅ Development Tools
- Local development server
- Database management via CLI
- Code generation (controllers, models, migrations)
- Testing framework (PHPUnit)
- Debugging tools

### ✅ Documentation
- 7 skill files covering all aspects
- AGENTS.md with project standards
- Local documentation copies
- Inline code comments
- Decision records

### ✅ Security Features
- CSRF protection
- XSS filtering
- SQL injection prevention (query builder)
- Password security validators
- Rate limiting
- Secure headers

## Getting Started: Your Turn

If this resonates with you, here's how to start your own Vibe Coding journey:

### Prerequisites (What You Actually Need)

**Hardware:**
- Any computer from the last 5 years
- 4GB RAM minimum (8GB recommended)
- Internet connection (for downloading, not for working)

**Skills:**
- Basic computer literacy (files, folders, installing software)
- Ability to read and follow instructions
- Curiosity and persistence
- Willingness to ask questions

**Time:**
- 1-2 hours per day for 2-3 weeks to get comfortable
- Then it accelerates dramatically

### Step-by-Step First Steps

**Week 1: Environment Setup**

1. **Install PHP** (php.net)
   - Windows: Download installer
   - Mac: Built-in or Homebrew
   - Linux: Package manager

2. **Install Composer** (getcomposer.org)
   - One command or installer
   - This is your package manager

3. **Install a Code Editor**
   - VS Code (free, recommended)
   - Or PHPStorm (paid but excellent)
   - Or OpenCode (with AI built-in)

4. **Download CodeIgniter 4**
   - Via Composer: `composer create-project codeigniter4/appstarter myproject`
   - Or download from codeigniter.com

5. **Test it**
   - Run: `php spark serve`
   - Open browser: http://localhost:8080
   - You should see the welcome page

**Week 2: Learn the Basics**

1. **Read the CodeIgniter tutorial**
   - Build their example blog
   - Don't just copy—understand why

2. **Play with the AI**
   - Set up OpenCode or similar
   - Ask it to explain the code you're reading
   - Get comfortable with the conversation

3. **Build something tiny**
   - A to-do list API
   - Just create, read, update, delete
   - Don't worry about auth yet

**Week 3: Add Authentication**

1. **Install Shield**
   - `composer require codeigniter4/shield`
   - `php spark shield:setup`
   - `php spark migrate --all`

2. **Protect your endpoints**
   - Add the token filter to your routes
   - Test with a tool like Postman or curl

3. **Document your decisions**
   - Start your own AGENTS.md
   - Write down why you did things

**Week 4+: Build Your Real Project**

Now you're ready to build your actual app. You have:
- A working local environment
- Basic understanding of the framework
- AI assistance configured
- Authentication ready
- The Vibe Coding methodology

### Resources to Help You

**Official Documentation:**
- CodeIgniter 4 User Guide: https://codeigniter.com/user_guide/
- Shield Documentation: https://shield.codeigniter.com/
- PHP Documentation: https://www.php.net/docs.php

**Communities:**
- CodeIgniter Forum: forum.codeigniter.com
- Reddit: r/codeigniter and r/PHPhelp
- Discord: Many PHP and CI4 servers

**Tools:**
- OpenCode: AI coding assistant
- Postman: API testing
- TablePlus: Database management
- Git: Version control

### Mindset Shifts

**From: "I need to learn everything before I start"**
**To: "I'll learn what I need as I build"**

You don't need to be an expert to be productive. Learn the 20% that gives you 80% of the results. The rest comes with time.

**From: "Mistakes are bad"**
**To: "Mistakes are how I learn"**

Every error message teaches you something. Every bug makes you better. The AI helps you recover quickly.

**From: "I need permission to build"**
**To: "I can figure this out"**

No one gave us permission. We just started. You can too.

## Conclusion: Your Idea Deserves to Exist

If you've read this far, you have something you want to build. A problem you want to solve. A change you want to make in the world.

The technology shouldn't stop you.

Yes, there's a learning curve. Yes, you'll get stuck sometimes. Yes, it takes effort.

But it's not magic. It's not reserved for people with computer science degrees. It's a skill you can learn, and AI makes it accessible faster than ever before.

We built LaunchPad API in days, not months. We documented every decision so we (and you) can understand the reasoning. We created a foundation that we can build on for years.

You can do this too.

Start small. Ask questions. Break things and fix them. Let the AI guide you. Document what you learn.

The barrier to entry has never been lower. The tools have never been better. The time to start is now.

**Your idea deserves to exist. Go build it.**

---

## About This Guide

This article documents the real process we used to build LaunchPad API, a production-ready API foundation using CodeIgniter 4, Shield authentication, and OpenCode AI assistance.

**Project Location**: `/`

**Technical Stack**:
- PHP 8.2+
- CodeIgniter 4
- Shield Authentication
- MySQL (production) / SQLite (development)
- Composer dependency management

**Files Referenced**:
- `AGENTS.md` - Project guidelines and decision documentation
- `.opencode/skills/*.md` - AI knowledge files
- `composer.json` - Project dependencies

**Last Updated**: February 17, 2026

---

*Have questions? Building your own project? Connect with us—we'd love to hear about what you're creating.*
