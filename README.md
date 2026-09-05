<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>System Security Scanner</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    background: #050505;
    color: #00ff66;
    font-family: Consolas, Arial, sans-serif;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
}

.container {
    width: 92%;
    max-width: 650px;
    border: 1px solid #00ff66;
    background: #080808;
    padding: 25px;
    box-shadow: 0 0 25px rgba(0,255,100,.25);
}

.header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid #174d2c;
    padding-bottom: 15px;
}

.logo {
    font-size: 22px;
    font-weight: bold;
}

.warning {
    color: #ff3333;
    animation: blink .7s infinite;
}

@keyframes blink {
    50% { opacity: .3; }
}

h1 {
    font-size: 24px;
    margin-bottom: 8px;
}

.status {
    color: #aaa;
    min-height: 22px;
}

.bar {
    width: 100%;
    height: 24px;
    background: #151515;
    border: 1px solid #236b3c;
    margin: 25px 0 10px;
}

.progress {
    width: 0%;
    height: 100%;
    background: #00ff66;
    box-shadow: 0 0 12px #00ff66;
    transition: width .1s linear;
}

.percent {
    text-align: right;
    font-size: 18px;
}

.info {
    margin-top: 25px;
    padding: 15px;
    background: #0d0d0d;
    border: 1px solid #222;
    color: #777;
    font-size: 13px;
    line-height: 1.7;
}

.fake-log {
    height: 120px;
    overflow: hidden;
    margin-top: 20px;
    padding: 10px;
    background: #020202;
    border: 1px solid #151515;
    font-size: 12px;
    color: #00aa44;
}

.exit {
    margin-top: 18px;
    background: transparent;
    border: 1px solid #555;
    color: #777;
    padding: 8px 15px;
    cursor: pointer;
}

.exit:hover {
    color: white;
    border-color: white;
}

#result {
    display: none;
    text-align: center;
}

.gotcha {
    font-size: 45px;
    color: #00ff66;
}

.sub {
    color: #aaa;
}
</style>
</head>

<body>

<div class="container" id="scanner">

    <div class="header">
        <div class="logo">◉ SYSTEM SECURITY</div>
        <div class="warning">● SCANNING</div>
    </div>

    <h1>Security Threat Detection</h1>

    <p class="status" id="status">
        Initializing security scan...
    </p>

    <div class="bar">
        <div class="progress" id="progress"></div>
    </div>

    <div class="percent" id="percent">0%</div>

    <div class="fake-log" id="log">
        > Starting system analysis...<br>
        > Loading security modules...<br>
    </div>

    <div class="info">
        Scan duration: 60 seconds<br>
        System protection: ACTIVE<br>
        Network monitoring: ACTIVE<br>
        Threat database: UPDATED
    </div>

    <button class="exit" onclick="exitPrank()">Exit scan</button>

</div>


<div class="container" id="result">

    <div class="gotcha">😂 GOTCHA!</div>

    <h2>No virus was found.</h2>

    <p class="sub">
        This was only a harmless fake security scan.
    </p>

    <p class="sub">
        Nothing was downloaded, installed, changed, or scanned.
    </p>

</div>


<script>

let progress = 0;

const bar = document.getElementById("progress");
const percent = document.getElementById("percent");
const status = document.getElementById("status");
const log = document.getElementById("log");

const messages = [
    "Checking installed applications...",
    "Scanning system files...",
    "Analyzing network connections...",
    "Checking browser activity...",
    "Scanning temporary files...",
    "Checking storage integrity...",
    "Searching for suspicious activity...",
    "Analyzing security permissions...",
    "Finalizing security report..."
];

const fakeLogs = [
    "Analyzing system process...",
    "Checking application signatures...",
    "Examining temporary data...",
    "Checking network status...",
    "Analyzing browser processes...",
    "Verifying security permissions...",
    "Scanning system directories...",
    "Updating threat database...",
    "Checking background processes..."
];


/*
    60 SECOND SCAN

    60000 milliseconds / 100 steps
    = 600 milliseconds per step
*/

const timer = setInterval(() => {

    progress++;

    bar.style.width = progress + "%";
    percent.textContent = progress + "%";

    let messageIndex =
        Math.floor(progress / 100 * messages.length);

    if (messageIndex >= messages.length) {
        messageIndex = messages.length - 1;
    }

    status.textContent = messages[messageIndex];

    // Add fake activity to the log
    if (progress % 4 === 0) {

        const randomLog =
            fakeLogs[Math.floor(Math.random() * fakeLogs.length)];

        log.innerHTML +=
            "> " + randomLog + "<br>";

        log.scrollTop = log.scrollHeight;
    }

    // Finish
    if (progress >= 100) {

        clearInterval(timer);

        document.getElementById("scanner").style.display = "none";
        document.getElementById("result").style.display = "block";
    }

}, 600);


// Safe exit
function exitPrank() {

    clearInterval(timer);

    document.body.innerHTML = `
        <div style="
            color:#00ff66;
            font-family:Arial;
            text-align:center;
            padding:40px;
        ">

            <h1>Scan Stopped</h1>

            <p>
                Security scan was safely cancelled.
            </p>

        </div>
    `;
}

</script>

</body>
</html>
