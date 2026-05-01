# walled-garden
Plans and Instructions for setting up a home network, self hosting many services, and acheiving privacy.

## Home Network

### Router - Ubiquity UDM

1. Allows you to run WireGuard for a self-hosted VPN. Latency and speeds are essentially limited by your ISP speeds. (Fiber internet will be best)

### Compute Server

1. Local LLM (Ollama)
2. Local Git Server
    1. Forgejo - FOSS alternative to Gitea, high performance, low bloat, non-profit. Coded in Go, forked from Gitea in late 2022
    2. LFS on NAS
3. Local Discord Alternative (Matrix/Conduit)
    1. 
4. IoT Hub
5. Game Server Host

### NAS Storage Server

3 Copies, 2 on-site, 1 off-site

### Security Cameras

# Privacy

1. Data Brokers: Incogni
    1. Various places on the internet will collect and aggregate your personal information. This can include your legal name, social media profiles, online aliases, age, current and previous addresses, email addresses and phone numbers, and even a list of people you know (family, friends, coworkers, relationships, etc). Some nefarious sources may even track username and passwords that have been revealed in various breaches. Data brokers will hold and sell/distribute this information to various sources, whether for marketing purposes or something more nefarious. This exposes you to spam calls, spam mail, targeted marketing profiles, scams, etc. Even worse, because of the relational data,  These data brokers are legally required to allow you to request a copy of the data they have collected, and also to allow you to request for them to delete it. This becomes a complex process because there are tens of thousands of data brokers, and you don't know who has your data. Incogni can help with this by automating the data removal process and monitoring the legal follow-ups, but to gain true anonymity it requires some additional leg work.
3. Password Manager: KeePassXC
    1. A password manager can help with multiple things. First, it allows you to automatically generate complex passwords that are near-impossible to crack, and second it allows you to use a unique password for each account without running the risk of forgetting and even having the ability to securly autofill without risking security. This also helps with phising protection, since the password manager will check the URL before autofilling your credentials. The way your Password Manager will help your privacy (beyond security) is that it will allow you to keep a ledger off all websites that you have accounts with. When you move to erase your digital footprint, you can query the list of accounts registered in the database to find unused accounts, delete the account, and send data deletion requests to the host. After deletion, you can 
    2. **Desktop: KeePassXC** - Serves as the actual interface with the database file. You enter the master password to unlock it, then you can browse or query credentials.
    3. **Browser: KeePassXC-Browser** - Queries your local database from the browser
    4. **Mobile: KeePassium** - Downloads and syncs your database from a remote server for use on Mobile. This can be OneDrive, Dropbox, Google Drive, or a custom HTTP/S service.
    5. **Exposure Detection: Have I Been Pwned (HIBP)** - Checks the hash of your password against the hash of a list of exposed username/password combos to see if you need to reset.
4. Home Security Systems
    1. Ring Doorbell Alternative:  
5. VPN:
    1. **Remote (privacy): ProtonVPN** - Masks your identity, allows you to change your location, but internet speeds and latency will be heavily limited.
    2. **Home (local access): WireGuardVPN** - You are connecting to your home network from far away, it is securely encrypted, it allows you to access local things like printers, NAS storage, etc., and the speed/latency is only limited by your current internet and your home internet. While it is securly encrypted, it does not mask your identity or location. Your home ISP can still see what you are doing, and any internet traffic will look like it's coming to and from your home network. For instance, without this VPN your info would be visible to others in a coffee shop, or your employer's IT department, but with this VPN they would just see packets going to your house, then your home ISP would see packets coming from your device, then going to the other item. If you have locally hosted resources at home with End-to-End-Encryption (E2EE), then your ISP would not be able to decipher it.
    3. TODO: How can you automate the process of using a VPN for only certain services? For instance, only using a VPN to home when accessing a local git server, and nesting a ProtonVPN service underneath your WireGuardVPN service for things to mask your location?
6. Browser: Brave, Firefox, DuckDuckGo
    1. **Search Engine:** DuckDuckGo
    2. **Extensions:** Privacy Badger (block trackers), uBlockOrigin (block ads), DuckDuckGo Privacy Essentials (block and encrypt)
    3. Bonus: SleepyTabs (Save RAM usage by sleeping inactive tabs)
7. Messaging
    1. The general movement of the world seems to be heading towards some sort of surveillance. This involves identity checks, message filtering, etc. On the surface, one may think that this could lead to a safer internet, but you don't have to go far before you could see some instances of online policing of free speech. (COVID, "Fake News", "Hate Speech" laws in the UK, Cancel Culture, etc.) To circumvent this you will have to start relying on communication methods that don't require ID checks, and that offer E2EE. It will also help to obfuscate communication methods with aliases and support alternative, open-source platforms.
    2. **Email provider: ProtonMail** - GMail has historically scanned your emails for marketing purposes, however they claim to have stopped this around 2018. Despite this claim, they still have the capability to start doing this again in the future, and they already have started using AI to read the sender info, subject, and summarize the contents in the body text. This is especially relevant for bank statements, online payment receipts, and other personal info. ProtonMail offers E2EE emailing, provided that both ends have that capability, and has a firm commitment and reputation for privacy. The sender and recipient addresses, subject line, IP address, and timestamps are still visible to the server.
    3. ***Email aliasing***: SimpleLogin - An aliasing service will basically mask your email from outside sources. Think of the stories of military leaders finding leaks by giving every person a different version of the plan. Never give your primary email address to anyone. Instead, use an aliasing service to generate a proxy address, emails going to this proxy alias will be forwarded to your primary, completely hidden from the other party. Use an aliasing service like SimpleLogin, then use a password manager like KeePassXC to remember which one you assigned. If this email starts receiving spam, you know that someone you gave this proxy alias to has shared it, leaked it, or had a data breach. Usually you get around 10 aliases for free, but with a paid subscription you could have unlimited. If one alias becomes compromized, simply scrap the alias and note who had access to that email to see how it was leaked.
    4. **E2EE Discord Alternative: Matrix** - Discord has recently made a large push for implementing ID verification in the name of "Youth Safety". In reality this is a ploy for surveillance and censorship. The response to this led to a mass search for alternatives. One of the most popular options is Matrix. It requires a bit more technical prowess to get set up, but it offers E2EE and self hosting data ownership. Rather than having to connect to centralized Discord Servers, this alternative is "Federated", meaning that it functions as a vast network of independent servers that function as nodes. This is closer to email than anything else, as the user will make an account through some domain, which can be self hosted, or you can pick from an existing public one. If you self host, you can set your own limits for file size limits, bandwidth limits, etc, without having to pay for Nitro.
        1. Server option: Conduit
        2. Desktop Client: TBD
        3. Mobile Client: Element X
        4. Apps/Plugins
            1. Text
            2. Video Call
            3. Screen Share
            4. Whiteboard
            5. Watch Together
            6. Music integration
            7. Games? (Chess)
8. Perform Destructive Obfuscation: Everything else can be done before transitioning completely, think of it as testing the waters before jumping in. This is where you start untangling your actual accounts and data connections.
    1. Operating System Ecosystem: Turn off web and app activity tracking, location history, ad personalization. Then delete historical data.
        1. Google
        2. Apple
        3. Microsoft
        4. etc.
    2. Check Social Media
        2. Instagram: 
        3. Facebook
        4. Threads
        5. X (Twitter)
        6. Snapchat
        7. GroupMe
        8. Discord
        9. Reddit: User Settings -> Safety & Privacy -> Authorized Applications
        10. Twitch: Profile Pic -> Settings -> Connections. Disconnect all publishers and social links
        11. Xbox: 
        12. Steam
    3. Bonus: Poison the archives - Use a tool like Redact, Power Delete Suite, or Shreddit. This allows obfuscation before deletion, so that you can poison AI scrapers and online archives. 
9. Recommended: Swap to Linux if feasible (at least take some time to know how it works, so you aren't hopeless if it becomes necessary).
