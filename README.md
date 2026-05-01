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
    1. A password manager can help with multiple things. First, it allows you to automatically generate complex passwords that are near-impossible to crack, and second it allows you to use a unique password for each account without running the risk of forgetting and even having the ability to securly autofill without risking security. This also helps with phising protection, since the password manager will check the URL before autofilling your credentials. 
    2. Desktop: KeePassXC - Serves as the actual interface with the database file. You enter the master password to unlock it, then you can browse or query credentials.
    3. Browser: KeePassXC-Browser - Queries your local database from the browser
    4. Mobile: KeePassium - Downloads and syncs your database from a remote server for use on Mobile. This can be OneDrive, Dropbox, Google Drive, or a custom HTTP/S service.
    5. Exposure Detection: Have I Been Pwned (HIBP) - Checks the hash of your password against the hash of a list of exposed username/password combos to see if you need to reset.
4. VPN:
    1. Remote (privacy): ProtonVPN - Masks your identity, allows you to change your location, but internet speeds and latency will be heavily limited.
    2. Home (local access): WireGuardVPN - You are connecting to your home network from far away, it is securely encrypted, it allows you to access local things like printers, NAS storage, etc., and the speed/latency is only limited by your current internet and your home internet. While it is securly encrypted, it does not mask your identity or location. Your home ISP can still see what you are doing, and any internet traffic will look like it's coming to and from your home network. For instance, without this VPN your info would be visible to others in a coffee shop, or your employer's IT department, but with this VPN they would just see packets going to your house, then your home ISP would see packets coming from your device, then going to the other item. If you have locally hosted resources at home with End-to-End-Encryption (E2EE), then your ISP would not be able to decipher it.
    3. TODO: How can you automate the process of using a VPN for only certain services? For instance, only using a VPN to home when accessing a local git server, and nesting a ProtonVPN service underneath your WireGuardVPN service for things to mask your location?
5. Browser: Brave, Firefox, DuckDuckGo
    1. Search Engine: DuckDuckGo
    2. Extensions: Privacy Badger (block trackers), uBlockOrigin (block ads), DuckDuckGo Privacy Essentials (block and encrypt)
    3. Bonus: SleepyTabs (Save RAM usage by sleeping inactive tabs)
6. Messaging
    1. The general movement of the world seems to be heading towards some sort of surveillance. This involves identity checks, message filtering, etc. On the surface, one may think: "If I have nothing to hide, why should I care?" The concern comes from the potential for future shifts in culture or speech laws.
    2. Email provider: ProtonMail
    3. Email aliasing: SimpleLogin
    4. E2EE Discord: Matrix
