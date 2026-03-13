---
title: "Dipcoin Vault Dashboard - TRUMP"
tags: ["dashboard", "sui", "crypto"]
---

<div class="dashboard-container">
  <div class="hero-section">
    <div class="hero-badge">Live On-Chain Data</div>
    <h1 class="hero-title">Dipcoin Vault</h1>
    <p class="hero-subtitle">TRUMP Fund Performance & Analytics</p>
    <a href="https://suivision.xyz/object/0xbb2d338ca65598657031429c619740f8fd78755ada63027c2805500b422faa09" target="_blank" class="explorer-btn">
      View on SuiVision ↗
    </a>
  </div>

  <div class="loading-state" id="loading-spinner">
    <div class="spinner"></div>
    <p>Syncing with Sui Mainnet...</p>
  </div>

  <div class="metrics-grid" id="metrics-container" style="display: none;">
    
    <!-- Card 1: Object ID -->
    <div class="metric-card">
      <div class="card-icon">🆔</div>
      <div class="card-label">Object ID</div>
      <div class="card-value id-value" id="val-id" onclick="copyToClipboard('0xbb2d338ca65598657031429c619740f8fd78755ada63027c2805500b422faa09')">
        0xbb2d...aa09
        <span class="copy-hint">Copy</span>
      </div>
    </div>

    <!-- Card 2: Object Type -->
    <div class="metric-card">
      <div class="card-icon">📦</div>
      <div class="card-label">Module Type</div>
      <div class="card-value type-value" id="val-type">--</div>
    </div>

    <!-- Card 3: Status / Owner -->
    <div class="metric-card">
      <div class="card-icon">👑</div>
      <div class="card-label">Ownership</div>
      <div class="card-value" id="val-owner">--</div>
    </div>

    <!-- Card 4: Version -->
    <div class="metric-card">
      <div class="card-icon">🔄</div>
      <div class="card-label">Object Version</div>
      <div class="card-value" id="val-version">--</div>
    </div>
  </div>

  <!-- Dynamic Fields Section -->
  <div class="details-section" id="details-container" style="display: none;">
    <h2>Vault State</h2>
    <div class="fields-list" id="fields-list">
      <!-- Injected via JS -->
    </div>
  </div>
</div>

<style>
/* Apple/Google Inspired Minimalist Theme */
.dashboard-container {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem 0;
  color: #1d1d1f;
}

/* Dark mode support for Quartz */
:root[saved-theme="dark"] .dashboard-container {
  color: #f5f5f7;
}

.hero-section {
  text-align: center;
  margin-bottom: 4rem;
  padding: 3rem 2rem;
  background: linear-gradient(145deg, rgba(245,245,247,0.5) 0%, rgba(255,255,255,0.8) 100%);
  border-radius: 24px;
  backdrop-filter: blur(20px);
  -webkit-backdrop-filter: blur(20px);
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.04);
  border: 1px solid rgba(0,0,0,0.05);
}

:root[saved-theme="dark"] .hero-section {
  background: linear-gradient(145deg, rgba(30,30,32,0.5) 0%, rgba(40,40,42,0.8) 100%);
  border: 1px solid rgba(255,255,255,0.05);
}

.hero-badge {
  display: inline-block;
  background: rgba(0, 122, 255, 0.1);
  color: #007aff;
  padding: 6px 16px;
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  letter-spacing: 0.5px;
  margin-bottom: 1rem;
  text-transform: uppercase;
}

.hero-title {
  font-size: 3rem !important;
  font-weight: 700;
  margin: 0 0 0.5rem 0 !important;
  background: -webkit-linear-gradient(45deg, #1d1d1f, #434344);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  letter-spacing: -1px;
}

:root[saved-theme="dark"] .hero-title {
  background: -webkit-linear-gradient(45deg, #f5f5f7, #a1a1a6);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hero-subtitle {
  font-size: 1.2rem;
  color: #86868b;
  margin-bottom: 2rem;
}

.explorer-btn {
  display: inline-block;
  background: #1d1d1f;
  color: #fff !important;
  padding: 12px 28px;
  border-radius: 98px;
  font-weight: 500;
  text-decoration: none !important;
  transition: all 0.3s ease;
  font-size: 1rem;
}

:root[saved-theme="dark"] .explorer-btn {
  background: #f5f5f7;
  color: #1d1d1f !important;
}

.explorer-btn:hover {
  transform: scale(1.02);
  box-shadow: 0 8px 16px rgba(0,0,0,0.1);
}

/* Grid Layout */
.metrics-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 1.5rem;
  margin-bottom: 3rem;
}

.metric-card {
  background: #ffffff;
  padding: 1.5rem;
  border-radius: 20px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.03);
  border: 1px solid rgba(0,0,0,0.04);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  display: flex;
  flex-direction: column;
}

:root[saved-theme="dark"] .metric-card {
  background: #1c1c1e;
  border: 1px solid rgba(255,255,255,0.05);
}

.metric-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 30px rgba(0,0,0,0.08);
}

.card-icon {
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.card-label {
  font-size: 0.85rem;
  color: #86868b;
  font-weight: 500;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  margin-bottom: 0.5rem;
}

.card-value {
  font-size: 1.2rem;
  font-weight: 600;
  word-break: break-all;
}

.id-value {
  color: #007aff;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.type-value {
  font-size: 1rem;
  line-height: 1.4;
}

.copy-hint {
  font-size: 0.7rem;
  background: rgba(0,122,255,0.1);
  padding: 2px 8px;
  border-radius: 10px;
  opacity: 0;
  transition: opacity 0.2s;
}

.id-value:hover .copy-hint {
  opacity: 1;
}

/* Dynamic Details Section */
.details-section {
  background: #ffffff;
  border-radius: 24px;
  padding: 2.5rem;
  box-shadow: 0 4px 24px rgba(0,0,0,0.03);
  border: 1px solid rgba(0,0,0,0.04);
}

:root[saved-theme="dark"] .details-section {
  background: #1c1c1e;
  border: 1px solid rgba(255,255,255,0.05);
}

.details-section h2 {
  margin-top: 0 !important;
  margin-bottom: 1.5rem !important;
  font-size: 1.5rem;
  font-weight: 600;
}

.field-row {
  display: flex;
  justify-content: space-between;
  padding: 1rem 0;
  border-bottom: 1px solid rgba(0,0,0,0.05);
}

:root[saved-theme="dark"] .field-row {
  border-bottom: 1px solid rgba(255,255,255,0.05);
}

.field-row:last-child {
  border-bottom: none;
}

.field-key {
  font-weight: 500;
  color: #86868b;
}

.field-val {
  font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
  font-size: 0.9rem;
  font-weight: 500;
  max-width: 60%;
  text-align: right;
  word-break: break-all;
}

/* Loading Spinner */
.loading-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 4rem 0;
  color: #86868b;
}

.spinner {
  width: 40px;
  height: 40px;
  border: 3px solid rgba(0,122,255,0.2);
  border-top-color: #007aff;
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin-bottom: 1rem;
}

@keyframes spin { 
  to { transform: rotate(360deg); } 
}
</style>

<script>
const OBJECT_ID = "0xbb2d338ca65598657031429c619740f8fd78755ada63027c2805500b422faa09";
const RPC_URL = "https://fullnode.mainnet.sui.io:443";

async function fetchVaultData() {
  const payload = {
    jsonrpc: "2.0",
    id: 1,
    method: "sui_getObject",
    params: [
      OBJECT_ID,
      {
        showType: true,
        showContent: true,
        showOwner: true,
        showPreviousTransaction: true
      }
    ]
  };

  try {
    const response = await fetch(RPC_URL, {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(payload)
    });
    
    const json = await response.json();
    
    if (json.error || !json.result || !json.result.data) {
      throw new Error("Failed to load object data from RPC.");
    }

    const data = json.result.data;
    renderData(data);
    
  } catch (error) {
    console.error("Error fetching Sui data:", error);
    document.getElementById("loading-spinner").innerHTML = `
      <div style="color: #ff3b30; text-align: center;">
        <div style="font-size: 2rem; margin-bottom: 1rem;">⚠️</div>
        <p>Failed to connect to Sui Mainnet.</p>
        <p style="font-size: 0.8rem; opacity: 0.7;">${error.message}</p>
      </div>
    `;
  }
}

function renderData(data) {
  // Hide spinner, show content
  document.getElementById("loading-spinner").style.display = "none";
  document.getElementById("metrics-container").style.display = "grid";
  document.getElementById("details-container").style.display = "block";

  // Format Type (extract the module name and struct)
  const fullType = data.type || "Unknown";
  const typeParts = fullType.split("::");
  const shortType = typeParts.length > 2 ? `${typeParts[1]}::${typeParts[2].split("<")[0]}` : fullType;
  document.getElementById("val-type").innerText = shortType;
  document.getElementById("val-type").title = fullType;

  // Format Owner
  let ownerText = "Shared / Immutable";
  if (data.owner) {
    if (data.owner.AddressOwner) {
      const addr = data.owner.AddressOwner;
      ownerText = `${addr.slice(0, 6)}...${addr.slice(-4)}`;
    } else if (data.owner.Shared) {
      ownerText = "Shared Object";
    }
  }
  document.getElementById("val-owner").innerText = ownerText;

  // Version
  document.getElementById("val-version").innerText = data.version || "--";

  // Dynamic Fields Mapping
  if (data.content && data.content.fields) {
    const fields = data.content.fields;
    const listHtml = Object.entries(fields).map(([key, val]) => {
      // Ignore id field as we already show it
      if (key === "id") return "";
      
      let displayVal = val;
      if (typeof val === "object") {
        displayVal = JSON.stringify(val);
      }
      
      return `
        <div class="field-row">
          <div class="field-key">${formatKey(key)}</div>
          <div class="field-val" title='${displayVal}'>
            ${truncateValue(displayVal)}
          </div>
        </div>
      `;
    }).join("");
    
    document.getElementById("fields-list").innerHTML = listHtml || "<p>No readable fields found.</p>";
  }
}

function formatKey(key) {
  return key.replace(/_/g, " ").replace(/\b\w/g, l => l.toUpperCase());
}

function truncateValue(val) {
  const str = String(val);
  if (str.length > 30) {
    return str.slice(0, 15) + "..." + str.slice(-10);
  }
  return str;
}

function copyToClipboard(text) {
  navigator.clipboard.writeText(text).then(() => {
    const hint = document.querySelector('.copy-hint');
    hint.innerText = "Copied!";
    hint.style.background = "rgba(52, 199, 89, 0.1)";
    hint.style.color = "#34c759";
    setTimeout(() => {
      hint.innerText = "Copy";
      hint.style.background = "rgba(0,122,255,0.1)";
      hint.style.color = "inherit";
    }, 2000);
  });
}

// Auto-refresh data every 30 seconds
document.addEventListener("DOMContentLoaded", () => {
  fetchVaultData();
  setInterval(fetchVaultData, 30000);
});
</script>