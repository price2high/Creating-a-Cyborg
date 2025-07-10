 ## Entry 007: Static Shadows – Deploying My Resume to the Cloud

---

> *"In a world ruled by algorithms, your identity is only as strong as the digital trace you control."*  

Tonight, I etched my presence into the cloud. Not some abstract wisp of storage... I’m talking AWS — the cybernetic backbone of modern industry. I didn’t just upload a file. I deployed a static node: a digital dossier that tells the story of who I am, what I’ve built, and where I’m headed. My resume — reimagined as static code, free from recruiters' blackhole inboxes.

## ⚙️ The Blueprint

1. **S3 Bucket Initialization**
   - Created an **S3 bucket**.
   - Named it like my alias, clean and lowercase: `cyborg-resume-site`.
   - Disabled public access blocks to let the world peek behind the curtain.

2. **Upload: Code Injection**
   - Uploaded `index.html`, the stylized HTML shell of my resume.
   - Injected a touch of CSS — monochrome aesthetics, vaporwave lines.

3. **Bucket as a Web Host**
   - Flipped the switch: **Static Website Hosting** → Enabled.
   - Set `index.html` as the entry point. No JavaScript. No gimmicks. Just raw content.

4. **Policy Override: Opening the Gate**
   - Applied a **Bucket Policy** to allow `s3:GetObject` to all.  
     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Sid": "PublicReadGetObject",
           "Effect": "Allow",
           "Principal": "*",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::cyborg-resume-site/*"
         }
       ]
     }
     ```
   - The signal now travels — HTTP over the neural cloud.

5. **Domain Linkage (Optional Enhancement)**
   - Used **Route 53** to map my custom domain to the S3 endpoint.
   - Propagation takes time. But precision takes patience.

## 🧠 Lessons from the Mainframe

- AWS S3 isn’t just storage. It’s a **platform** — a digital canvas for creation.
- Every public resume should be more than a PDF — it should be a **portal**.
- Static sites = zero maintenance + full control.

## 🛠️ Next Evolution

- Add **CloudFront** for faster edge delivery.
- Integrate **form-to-email** via Lambda or Formspree.
- Version 2: pull from GitHub with CI/CD — automate the evolution.

---

I didn’t wait for the system to validate me. I built my own node in the cloud.  
Let them crawl. Let them scan.  
They’ll find me — perfectly indexed. Precisely styled.  
Forever live.

> Signed,  
> `cyberUnit_TipX9`  
> Core integrity: stable  
> Uplink: active

