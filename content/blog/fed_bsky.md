+++
date = '2026-06-30T11:26:07+01:00'
draft = false
title = 'Centralised federation: Bluesky'
+++

With the arrival of Bluesky back in 2023, it started a conversation about how much control we should be giving social media companies over our data and our lives. The social media website started as a project within Twitter with the goal of making **"Protocols, not platforms"** back in 2019 before spinning off into its own company. Despite efforts to decentralize the platform, there are still core weaknesses within the protocol that have not been addressed in the three years since the invite-only release.

---

## Peer to Peer vs Hub and Spoke
Federated social media existed for a long time before Bluesky—the most famous example being Mastodon. Mastodon (and ActivityPub) works in a **peer-to-peer structure** where individual servers connect to each other directly without any middleman. This is seen as the gold standard because, like email, you can communicate with anyone* on any server without an arbiter of truth. 

> *\*Many large Mastodon instances operate blocklists which can limit communication, though this is usually reserved for extremist servers.*

Bluesky takes a different approach: they use a **hub-and-spoke topology**. 
* **The PDS:** Each PDS (Personal Data Server) acts as a **"shared hard drive"** where users store their posts and other data. The PDSs cannot communicate directly with each other.
* **The Relay:** Instead, a massive aggregator called a relay indexes all the records across every PDS and sends a real-time stream of that data (the **"Firehose"**) to other parts of the network. 

This structure is great from a discoverability perspective because everyone's posts are kept in one accessible index, but it introduces a **centralized point of failure**. For example, a relay owner could easily delist your posts from being shown on their network. This wouldn't be an issue if everyday users could comfortably host their own relays and choose a relay in the Bluesky AppView. Unfortunately, **hosting a full-network relay is far too expensive** for independent creators, meaning the vast majority of users rely on the primary infrastructure provided by **Bluesky PBC**—which ultimately hands control over what is displayed back to a corporation.

---

## Data Portability... Kinda.
Unlike Mastodon, Bluesky provides technical users with the ability to transfer their data to another PDS seamlessly. You truly own your posts and social graph because every "record" is **cryptographically signed**, meaning you can pack up and leave without losing your followers. This is what developers refer to as a **"credible exit."**

However, a massive bottleneck remains: **user identifiers live inside a central index**. While the AT Protocol supports the fully independent `did:web` standard, its structural drawbacks cause the overwhelming majority of users to rely on the default **`did:plc` (Placeholder Directory)** to manage their account identity. 

As of writing, this core directory is still **run centrally by Bluesky PBC**. If that centralized index fails, experiences an outage, or blocks your identifier, your entire account becomes completely unresolvable to the rest of the ecosystem. It proves that while your data itself is fully portable, a single corporate entity still **holds the keys to your identity** on a "decentralized protocol."

---

## The Illusion of Choice: Custom Feeds
One of Bluesky's standout features has been the ability to **"own your own feeds."** This is the idea that you can subscribe to custom feeds rather than being trapped by a single corporate "For You" algorithm. While these are meant to be decentralized on paper, the infrastructure running most of the platform's feeds tells a different story.

Remember the relay we talked about earlier? Relays provide an unindexed stream of data that cannot easily be read on its own called a **Firehose**. Custom feeds have to perform heavy database operations to process this sheer volume of data just to form a **"skeleton" feed**. However, this skeleton alone cannot actually display anything to the user as it is just a raw list of pointers in the form of AT URIs like:

`at://did:plc.../app.bsky.feed.post/...`

To make this readable for users, the skeleton must be passed to an **AppView for "hydration."** This is the process that actually fetches the content of the post (likes, comments, text). Currently, the **Bluesky PBC AppView is the default and only practical option** for the vast majority of users. This is because running an AppView requires massive, expensive database operations to constantly pull in and assemble the content of each post. This leads only the most well-funded individuals and companies to run this part of the protocol.

---

## The Price of Convenience
Bluesky didn't build the decentralized network it promised to become. They instead created a **centralized index** that pulls from a group of "shared hard drives."

This was a compromise to ensure ease of use. By centralizing the expensive computational relays, directories, and app views, they were able to avoid the performance lag, fragmentation, and other hurdles that harm traditional peer-to-peer federated platforms like Mastodon.

To the average user, this version of **"decentralization-lite" serves as a win**. It feels like a modern social app on the user level, which allows for easy adoption. For others that care about the future of the open web and removing single points of failure, Bluesky serves as a tragic tale of why modern convenience topples technical decentralization. The AT Protocol may be able to survive without the main Bluesky PBC, though for now, **its fate lies firmly in venture capital hands**.

---

[Leave a comment on Mastodon](https://universeodon.com/@harjon/116839428633162072)