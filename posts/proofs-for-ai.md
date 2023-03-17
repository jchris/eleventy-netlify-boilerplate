---
title: Why proofs matter for AI
metaDescription: This is a sample meta description. If one is not present in
  your page/post's front matter, the default metadata.description will be used
  instead.
date: 2023-03-17T18:13:08.530Z
author: J Chris Anderson
summary: Why contemplating our mortality can be a powerful catalyst for change
tags:
  - proofs
  - AI
  - architecture
  - cloudless
---

Generative and interactive AI is maturing rapidly, and the infrastructure it depends on was built to support the previous era of software. Provenance tracking, repeatability, and provability are becoming crucial for understanding program flows in new applications that chain multiple AI calls to get results. By using cryptographic content identifiers (CIDs) to refer to AI models, parameters, prompt inputs, and generated outputs, developers can more easily and reliably tune, improve, and debug AI workloads. Proofs play a crucial role in addressing these concerns, as they provide a method for verifying the accuracy of data and enabling efficient AI workflows. Keep reading to learn about the real-world implementations, benefits, and applications of proofs in AI.

## What is a proof, technically?

Cryptographic content identifiers (CIDs) enable developers to reference AI models, parameters, prompt inputs, and generated outputs with confidence in their provenance. CIDs are simply the hash of the data they represent. This means any data you can think of, from a movie file to a business card, already has a CID which anyone can find by using math functions so common they are built into computer chips. No matter how big or complext a piece of data, the CID is the same size, and it's self-verifying. That means if someone gives you a CID, you can "ask the internet" and if anyone has the content which matches it, you can get a copy from them and you don't have to trust them to trust you got what you were asking for. Neat huh? This basic technique powers a lot of software, from databases to image hosting sites to web accelerators.

Merkle hash trees make it easy to check if a small piece of data is part of a bigger set, and they do this quickly and securely. Imagine a tree where each leaf is a small chunk of data. You can create a unique fingerprint, or hash, for each chunk. Then, combine pairs of fingerprints and create a new hash for each pair. Keep doing this until you reach the root, creating a single hash that represents the whole tree. This root hash is like a summary of all the data in the tree. Anyone who has the root hash can validate if their copy of the entire tree is untampered with -- any changes and the root hash won't match.

Now, let's say you want to check if a small piece of data is part of this big set. You don't need the whole tree—just the fingerprints you used to create the top hash. With only a few of these, you can recreate the top hash and confirm that the data is part of the set. This is super useful in AI because it speeds up tasks like analyzing data and making decisions. Plus, it's perfect for areas where you need quick, accurate results, like healthcare and cybersecurity. Merkle hash trees help make AI solutions more reliable, secure, and efficient, allowing AI workloads to be used in situations where trust and accountability are paramount.

## How the experts use proofs

Hashes serve as a fundamental building block of everyday computing, extending far beyond their use in Merkle proofs. These compact digital fingerprints help ensure data integrity, uniqueness, and consistency across various computing processes. As a versatile and efficient tool, hashes play a significant role in diverse applications such as data storage, retrieval, and verification. Let's explore how hashes are deeply embedded in the various layers of caching and integrity checks, both on a single computer and across the network.

When a piece of data is requested by a program, it goes through multiple layers of caching and integrity checks before reaching the disk. Let's trace this journey from code to disk on a single machine. The process begins with the program looking for the requested data in the Level 1 (L1) cache, an ultra-fast yet minuscule cache nestled right inside the processor chip. If the data is not found there, the search continues to the Level 2 (L2) and Level 3 (L3) caches, which boast larger capacities but are slightly slower due to their increased distance from the core computation—every nanosecond counts in this high-speed world. At each cache stop, integrity checks are conducted to ensure the data remains untainted by electrical irregularities or even cosmic rays. Failing to locate the data in these on-chip caches, the search extends to the Level 4 (L4) cache, typically housed within the system's main memory. Here, too, integrity checks are performed before accessing the data. Finally, if none of the cache layers yield the requested data, the process reaches the disk controller cache and, ultimately, the disk itself, where the data is retrieved and verified for accuracy and consistency.

The same concept of caching and integrity checking applies to data requests across a network. Starting at the fast, local cache in a user's browser, the system verifies the data's integrity before moving on to the next layer. If the data is not found in the local cache, the request continues to the network cache layers, such as HTTP caches, Memcached, or server filesystem caches. At each stage, integrity checks are performed to ensure that the data is accurate and has not been tampered with. This layered approach to caching and integrity checks allows for quick, efficient, and reliable data retrieval in both single-machine and networked environments.

Proofs play a critical role in these network requests as well. When a secure connection is established between your computer and a website, a handshake process verifies the website's identity before creating a secret communication channel. The secure connection is the easy part, but how do you decide if it's really them?

To determine if the website is genuine, a process known as certificate verification is used. The website provides a digital certificate issued by a trusted organization called a Certificate Authority (CA). This digital certificate contains information about the website, such as its domain name, and a public key for encryption. The certificate is also digitally signed by the CA, which serves as a proof of its authenticity.

Your computer checks the certificate's digital signature using the CA's public key, which is stored in your browser or operating system. If the signature is valid, your computer then verifies that the certificate is issued to the website you're trying to visit. Once these checks are completed successfully, your computer trusts the website's identity and proceeds with the secure connection.

This certificate verification process relies on a chain of trust, with proofs and digital signatures at each step, ensuring that you're connecting to the authentic website and not an imposter. This is just another example of how proofs are an essential part of our everyday digital interactions.

# How proofs help for AI

Merkle tree proofs can reduce costs and accelerate data science workloads by allowing the reuse of unchanged data pipeline results automatically. By creating a tamper-proof data structure that stores intermediate results and their relationships, any modification in the data pipeline only requires recomputing the affected parts, while the rest of the results remain intact and reusable. This efficient approach not only saves time and computational resources but also makes debugging and auditing more powerful when working with AI training sets and model outputs. Leveraging a proofs-based approach ensures data integrity, making it easier to identify and trace any discrepancies or issues, which ultimately leads to improved AI model reliability and robustness.

The application of proofs in artificial intelligence leads to significant improvements in the reliability and accuracy of models while promoting reusability. Proofs enable proper sharing and collaboration, which are crucial in the AI field, by making it easier to verify and reproduce experimental results. This streamlined sharing and downstream use of data and models accelerates progress in AI and brings us closer to unlocking its full potential. Furthermore, using proofs to improve the reproducibility of AI-generated outputs allows for better model debugging and engineering. By incorporating prompts, random seeds, and model details in the proof Merkle hash, people can demonstrate that specific outputs originated from a particular session. This traceability not only fosters the sharing of AI-generated outputs but also bolsters the security, efficiency, and transparency of AI and distributed systems, making proofs an indispensable component of AI development.



