
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Trial Administrator - Copy Tool</title>

<style>
    body {
        margin: 0;
        padding: 40px 20px;
        font-family: Arial, sans-serif;
        background: #10141c;
        color: #ffffff;
    }

    .container {
        max-width: 650px;
        margin: auto;
    }

    h1 {
        text-align: center;
        font-size: 25px;
        margin-bottom: 8px;
    }

    .subtitle {
        text-align: center;
        color: #929baa;
        margin-bottom: 35px;
    }

    .copy-box {
        background: #1b2330;
        border: 1px solid #303c4d;
        border-radius: 12px;
        padding: 22px;
        margin-bottom: 20px;
    }

    .copy-box h3 {
        margin-top: 0;
        font-size: 16px;
        color: #8bbcff;
    }

    .message {
        background: #111821;
        border: 1px solid #303c4d;
        border-radius: 7px;
        padding: 15px;
        line-height: 1.6;
        margin-bottom: 17px;
        color: #e5eaf1;
    }

    button {
        width: 100%;
        padding: 13px;
        border: none;
        border-radius: 7px;
        background: #2878dc;
        color: white;
        font-weight: bold;
        font-size: 14px;
        cursor: pointer;
        transition: 0.2s;
    }

    button:hover {
        background: #4190f5;
    }

    button.copied {
        background: #218653;
    }
</style>
</head>

<body>

<div class="container">

    <h1>Trial Administrator</h1>
    <p class="subtitle">Quick Copy & Paste Tool</p>

    <div class="copy-box">
        <h3>01 — Initial Greeting</h3>

        <div class="message" id="message1">
            Hello I'm Trial Administrator its_danielv2 -
            How can I help you today? (If i'm late say void)
        </div>

        <button onclick="copyText('message1', this)">
            COPY MESSAGE
        </button>
    </div>

    <div class="copy-box">
        <h3>02 — Additional Support</h3>

        <div class="message" id="message2">
            Anything else I can support you with today?
        </div>

        <button onclick="copyText('message2', this)">
            COPY MESSAGE
        </button>
    </div>

</div>

<script>
async function copyText(id, button) {
    const text = document.getElementById(id).innerText;

    try {
        await navigator.clipboard.writeText(text);

        button.textContent = "✓ COPIED!";
        button.classList.add("copied");

        setTimeout(() => {
            button.textContent = "COPY MESSAGE";
            button.classList.remove("copied");
        }, 1500);

    } catch (error) {
        const textarea = document.createElement("textarea");
        textarea.value = text;
        document.body.appendChild(textarea);
        textarea.select();
        document.execCommand("copy");
        textarea.remove();

        button.textContent = "✓ COPIED!";
        button.classList.add("copied");

        setTimeout(() => {
            button.textContent = "COPY MESSAGE";
            button.classList.remove("copied");
        }, 1500);
    }
}
</script>

</body>
</html>
