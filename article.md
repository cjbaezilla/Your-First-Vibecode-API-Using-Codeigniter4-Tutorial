# Vibe Coding Your First API: How We Built LaunchPad API in Days (Not Months)

*A real-world guide for entrepreneurs who want to build their backend without hiring a developer or drowning in technical complexity*

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
