# 🤖Ai Avatar Agent 

**Vedio Link** - [Watch](https://drive.google.com/file/d/1a5zFyhW6nJJIEabNY0MS44rdaFtGh9Gm/view?usp=drivesdk)


This repository demonstrates how to integrate **HeyGen Interactive Avatars** into a **Next.js** application using the official [HeyGen Streaming Avatar SDK](https://github.com/HeyGen-Official/StreamingAvatarSDK).

It allows you to:
- Start and stop interactive avatar sessions.
- Customize avatar and voice.
- Test HeyGen’s real-time streaming API in a local Next.js app.

---

## 🚀 Features
✅ Interactive Avatar Streaming  
✅ Voice & Avatar Customization  
✅ Token-based Authentication using API route  
✅ Ready-to-run Next.js app  
✅ TypeScript + Tailwind CSS  

---

## 🧠 Tech Stack
- [Next.js 14+ (App Router)](https://nextjs.org/)
- [TypeScript](https://www.typescriptlang.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [HeyGen Streaming Avatar SDK](https://github.com/HeyGen-Official/StreamingAvatarSDK)
- Node.js 18+  

---

## ⚙️ Getting Started

### 1️⃣ Clone this repository
```bash
git clone https://github.com/your-username/heygen-avatar-demo.git
cd heygen-avatar-demo
2️⃣ Install dependencies
bash
Copy code
npm install
3️⃣ Setup your environment variables
Create a file named .env.local in the root of your project and add the following:

ini
Copy code
HEYGEN_API_KEY=sk_V2_your_heygen_api_key_here
NEXT_PUBLIC_BASE_API_URL=https://api.heygen.com
⚠️ Important:

Don’t include quotes (" ") around the API key.

Restart the Next.js dev server after adding .env.local.

You can find your HeyGen API key here:
👉 HeyGen Settings → Subscriptions & API

4️⃣ (Optional) Add OpenAI API key (if you use GPT features)
If you want to connect avatar interactions to OpenAI, add this line in .env.local:

ini
Copy code
OPENAI_API_KEY=sk-your-openai-key
5️⃣ Run the development server
bash
Copy code
npm run dev
Then open →
🌐 http://localhost:3000

You should see the HeyGen Interactive Avatar Demo.

🧩 Folder Structure
csharp
Copy code
heygen-avatar-demo/
│
├── app/
│   ├── api/
│   │   └── get-access-token/
│   │       └── route.ts         # Server-side token generation
│   └── page.tsx                 # Main UI page
│
├── components/
│   ├── Input.tsx                # Input component
│   ├── NavBar.tsx               # Navigation bar
│   ├── AvatarConfig/            # Avatar configuration UI
│   └── InteractiveAvatar.tsx    # Avatar streaming logic
│
├── public/
│   └── demo.png
│
├── package.json
└── README.md
🔐 API Route Example
Here’s how the API route securely generates a token using your HeyGen API key:

ts
Copy code
// /app/api/get-access-token/route.ts
export async function POST() {
  const HEYGEN_API_KEY = process.env.HEYGEN_API_KEY;
  const baseApiUrl = process.env.NEXT_PUBLIC_BASE_API_URL;

  if (!HEYGEN_API_KEY) {
    return new Response("Missing API key", { status: 500 });
  }

  try {
    const res = await fetch(`${baseApiUrl}/v1/streaming.create_token`, {
      method: "POST",
      headers: {
        "x-api-key": HEYGEN_API_KEY,
        "Content-Type": "application/json",
      },
    });

    const data = await res.json();
    return new Response(data.data.token, { status: 200 });
  } catch (error) {
    console.error("Error retrieving token:", error);
    return new Response("Failed to get access token", { status: 500 });
  }
}
🧠 How to Use the Demo
1️⃣ Click Start Session to create an avatar session.
2️⃣ The avatar will appear and start interacting.
3️⃣ You can enter custom Avatar ID and Voice ID.
4️⃣ Close the session and start again to test different configurations.

💡 How to Get Avatar and Voice IDs
Avatar IDs: labs.heygen.com/interactive-avatar

Voice IDs: HeyGen Voice API Docs

🧰 Troubleshooting
Issue	Fix
❌ API request failed with status 400	Invalid endpoint — check your route or base URL
❌ API request failed with status 401	Invalid or missing API key. Verify .env.local and restart server
❌ "API key missing" in console	.env.local not loaded or variable name typo
❌ Token not generated	Ensure you’re calling POST request from /api/get-access-token

🧾 License
This project is licensed under the MIT License.
Feel free to modify and use it for learning or internal demos.

🙌 Acknowledgements
Special thanks to:

HeyGen Official Team for the Interactive Avatar SDK.

Next.js for the web framework.

OpenAI for optional GPT integrations.

🧑‍💻 Author
Developed by Sachin Yadav
✨ “AI Avatar Agent” – Bringing Human-Like Interaction to Web Apps
