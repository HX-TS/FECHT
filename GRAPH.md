<!DOCTYPE html>

<html lang="en">

<head>

&#x20; <meta charset="UTF-8" />

&#x20; <meta name="viewport" content="width=device-width, initial-scale=1.0" />

&#x20; <meta name="theme-color" content="#f2efe9" />

&#x20; <title>FEC Hydrotest Live Dashboard</title>



&#x20; <style>

&#x20;   :root {

&#x20;     /\* Reference-image background only \*/

&#x20;     --bg: #f2efe9;



&#x20;     /\* Original dark dashboard theme \*/

&#x20;     --panel: #0d1820;

&#x20;     --panel-2: #111f29;

&#x20;     --panel-3: #162732;

&#x20;     --border: rgba(255, 255, 255, 0.10);

&#x20;     --grid: rgba(167, 187, 200, 0.16);

&#x20;     --text: #f7fafc;

&#x20;     --muted: #93a6b2;



&#x20;     --dwt: #31d08b;

&#x20;     --digital: #4d8dff;

&#x20;     --recorder: #a67cff;

&#x20;     --ambient: #ff9c42;

&#x20;     --water: #2bc7d1;

&#x20;     --accent: #ff7a00;

&#x20;     --danger: #ff6b6b;

&#x20;   }



&#x20;   \* { box-sizing: border-box; }

&#x20;   html { scroll-behavior: smooth; }



&#x20;   body {

&#x20;     margin: 0;

&#x20;     min-width: 320px;

&#x20;     min-height: 100vh;

&#x20;     color: var(--text);

&#x20;     background: var(--bg);

&#x20;     font-family: Inter, ui-sans-serif, system-ui, -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;

&#x20;   }



&#x20;   .page {

&#x20;     width: min(1560px, calc(100% - 28px));

&#x20;     margin: 14px auto 24px;

&#x20;   }



&#x20;   /\* =========================

&#x20;      ORIGINAL MODERN HEADER

&#x20;      ========================= \*/

&#x20;   .topbar {

&#x20;     display: grid;

&#x20;     grid-template-columns: minmax(0, 1fr) 410px;

&#x20;     overflow: hidden;

&#x20;     border: 1px solid var(--border);

&#x20;     border-radius: 18px;

&#x20;     background: var(--panel);

&#x20;     box-shadow: 0 18px 44px rgba(10, 18, 24, 0.16);

&#x20;   }



&#x20;   .brand-panel {

&#x20;     min-width: 0;

&#x20;     padding: 28px 32px 25px;

&#x20;     display: flex;

&#x20;     flex-direction: column;

&#x20;     justify-content: center;

&#x20;     background:

&#x20;       radial-gradient(circle at 8% 0%, rgba(77,141,255,.13), transparent 34%),

&#x20;       var(--panel);

&#x20;   }



&#x20;   h1 {

&#x20;     margin: 0;

&#x20;     max-width: 880px;

&#x20;     font-size: clamp(36px, 4.3vw, 66px);

&#x20;     line-height: .93;

&#x20;     letter-spacing: -0.045em;

&#x20;     text-transform: uppercase;

&#x20;     font-weight: 900;

&#x20;   }



&#x20;   .brand-word {

&#x20;     margin-top: 14px;

&#x20;     color: var(--muted);

&#x20;     font-size: 11px;

&#x20;     line-height: 1;

&#x20;     font-weight: 800;

&#x20;     letter-spacing: .42em;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .holding-panel {

&#x20;     border-left: 1px solid var(--border);

&#x20;     padding: 24px 24px 20px;

&#x20;     display: flex;

&#x20;     flex-direction: column;

&#x20;     justify-content: center;

&#x20;     background: var(--panel-2);

&#x20;   }



&#x20;   .holding-heading {

&#x20;     display: flex;

&#x20;     align-items: center;

&#x20;     gap: 9px;

&#x20;     margin-bottom: 13px;

&#x20;     font-size: 11px;

&#x20;     font-weight: 850;

&#x20;     letter-spacing: .07em;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .orange-dot {

&#x20;     width: 9px;

&#x20;     height: 9px;

&#x20;     flex: 0 0 auto;

&#x20;     border-radius: 50%;

&#x20;     background: var(--accent);

&#x20;     box-shadow: 0 0 0 5px rgba(255,122,0,.12);

&#x20;   }



&#x20;   .holding-row {

&#x20;     display: grid;

&#x20;     grid-template-columns: 1fr auto;

&#x20;     align-items: center;

&#x20;     gap: 14px;

&#x20;     min-height: 40px;

&#x20;     border-bottom: 1px solid var(--border);

&#x20;   }



&#x20;   .holding-label {

&#x20;     color: var(--muted);

&#x20;     font-size: 10px;

&#x20;     font-weight: 750;

&#x20;     letter-spacing: .045em;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .holding-value {

&#x20;     color: var(--text);

&#x20;     font-size: 18px;

&#x20;     font-weight: 900;

&#x20;     letter-spacing: .04em;

&#x20;     font-variant-numeric: tabular-nums;

&#x20;   }



&#x20;   .holding-value.remaining { color: #ffffff; }



&#x20;   .holding-dates {

&#x20;     display: grid;

&#x20;     grid-template-columns: 1fr 1fr;

&#x20;     gap: 16px;

&#x20;     margin-top: 11px;

&#x20;   }



&#x20;   .date-block:last-child { text-align: right; }



&#x20;   .date-label {

&#x20;     display: block;

&#x20;     margin-bottom: 3px;

&#x20;     color: var(--muted);

&#x20;     font-size: 9px;

&#x20;     font-weight: 750;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .date-value {

&#x20;     display: block;

&#x20;     font-size: 10px;

&#x20;     line-height: 1.35;

&#x20;     font-weight: 850;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .header-actions {

&#x20;     display: flex;

&#x20;     align-items: center;

&#x20;     justify-content: space-between;

&#x20;     gap: 10px;

&#x20;     margin-top: 13px;

&#x20;     padding-top: 12px;

&#x20;     border-top: 1px solid var(--border);

&#x20;   }



&#x20;   .status-pill {

&#x20;     min-width: 0;

&#x20;     color: var(--muted);

&#x20;     font-size: 9px;

&#x20;     line-height: 1.3;

&#x20;     font-weight: 750;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .refresh-button {

&#x20;     min-height: 36px;

&#x20;     padding: 0 13px;

&#x20;     border: 1px solid rgba(255,255,255,.14);

&#x20;     border-radius: 9px;

&#x20;     background: var(--panel-3);

&#x20;     color: var(--text);

&#x20;     cursor: pointer;

&#x20;     font-size: 9px;

&#x20;     font-weight: 850;

&#x20;     letter-spacing: .05em;

&#x20;     text-transform: uppercase;

&#x20;     transition: transform .15s ease, background .15s ease, border-color .15s ease;

&#x20;   }



&#x20;   .refresh-button:hover {

&#x20;     transform: translateY(-1px);

&#x20;     background: #1a303d;

&#x20;     border-color: rgba(255,255,255,.24);

&#x20;   }



&#x20;   .refresh-button:disabled { opacity: .45; cursor: wait; transform: none; }



&#x20;   /\* =========================

&#x20;      ORIGINAL MODERN CARDS

&#x20;      ========================= \*/

&#x20;   .chart-card {

&#x20;     margin-top: 14px;

&#x20;     overflow: hidden;

&#x20;     border: 1px solid var(--border);

&#x20;     border-radius: 18px;

&#x20;     background: var(--panel);

&#x20;     box-shadow: 0 18px 44px rgba(10, 18, 24, 0.13);

&#x20;   }



&#x20;   .card-header {

&#x20;     padding: 20px 20px 0;

&#x20;     border-bottom: 1px solid var(--border);

&#x20;     background: var(--panel);

&#x20;   }



&#x20;   .station-title-block {

&#x20;     padding: 0 2px 15px;

&#x20;     text-align: left;

&#x20;   }



&#x20;   .station-name {

&#x20;     margin: 0;

&#x20;     font-size: 22px;

&#x20;     line-height: 1;

&#x20;     font-weight: 900;

&#x20;     letter-spacing: -.025em;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .latest-data-status {

&#x20;     margin-top: 7px;

&#x20;     color: var(--muted);

&#x20;     font-size: 10px;

&#x20;     font-weight: 800;

&#x20;     letter-spacing: .045em;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .station-subtitle {

&#x20;     display: block;

&#x20;     margin-top: 6px;

&#x20;     color: #718792;

&#x20;     font-size: 11px;

&#x20;     font-weight: 600;

&#x20;   }



&#x20;   .metrics {

&#x20;     display: grid;

&#x20;     grid-template-columns: repeat(5, minmax(0, 1fr));

&#x20;     gap: 9px;

&#x20;     padding-bottom: 16px;

&#x20;   }



&#x20;   .metric {

&#x20;     position: relative;

&#x20;     min-width: 0;

&#x20;     min-height: 76px;

&#x20;     padding: 13px 13px 12px;

&#x20;     overflow: hidden;

&#x20;     border: 1px solid var(--border);

&#x20;     border-radius: 11px;

&#x20;     background: var(--panel-2);

&#x20;   }



&#x20;   .metric::before {

&#x20;     content: "";

&#x20;     position: absolute;

&#x20;     inset: 0 auto 0 0;

&#x20;     width: 3px;

&#x20;     background: var(--muted);

&#x20;   }



&#x20;   .metric.dwt::before { background: var(--dwt); }

&#x20;   .metric.digital::before { background: var(--digital); }

&#x20;   .metric.recorder::before { background: var(--recorder); }

&#x20;   .metric.ambient::before { background: var(--ambient); }

&#x20;   .metric.water::before { background: var(--water); }



&#x20;   .metric-label {

&#x20;     display: block;

&#x20;     margin-bottom: 8px;

&#x20;     color: var(--muted);

&#x20;     font-size: 9px;

&#x20;     font-weight: 800;

&#x20;     letter-spacing: .035em;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .metric-value {

&#x20;     color: var(--text) !important;

&#x20;     font-size: 19px;

&#x20;     font-weight: 900;

&#x20;     letter-spacing: -.02em;

&#x20;     font-variant-numeric: tabular-nums;

&#x20;   }



&#x20;   .chart-toolbar {

&#x20;     display: flex;

&#x20;     align-items: center;

&#x20;     justify-content: space-between;

&#x20;     gap: 16px;

&#x20;     padding: 12px 20px;

&#x20;     border-bottom: 1px solid var(--border);

&#x20;     background: var(--panel-2);

&#x20;   }



&#x20;   .legend {

&#x20;     display: flex;

&#x20;     align-items: center;

&#x20;     gap: 13px 18px;

&#x20;     flex-wrap: wrap;

&#x20;     color: #c4d0d6;

&#x20;     font-size: 9px;

&#x20;     font-weight: 800;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .legend-item {

&#x20;     display: inline-flex;

&#x20;     align-items: center;

&#x20;     gap: 7px;

&#x20;   }



&#x20;   .legend-line {

&#x20;     width: 25px;

&#x20;     height: 3px;

&#x20;     flex: 0 0 auto;

&#x20;     border-radius: 99px;

&#x20;   }



&#x20;   .legend-line.dwt { background: var(--dwt); }

&#x20;   .legend-line.digital { background: var(--digital); }

&#x20;   .legend-line.recorder { background: var(--recorder); }

&#x20;   .legend-line.ambient { background: var(--ambient); }

&#x20;   .legend-line.water { background: var(--water); }

&#x20;   .legend-item.unavailable { display: none; }



&#x20;   .data-info {

&#x20;     color: var(--muted);

&#x20;     font-size: 9px;

&#x20;     font-weight: 750;

&#x20;     text-align: right;

&#x20;     text-transform: uppercase;

&#x20;     white-space: nowrap;

&#x20;   }



&#x20;   .chart-wrap {

&#x20;     position: relative;

&#x20;     width: 100%;

&#x20;     height: 370px;

&#x20;     padding: 10px 12px 12px;

&#x20;     background: var(--panel);

&#x20;   }



&#x20;   canvas {

&#x20;     display: block;

&#x20;     width: 100%;

&#x20;     height: 100%;

&#x20;     border-radius: 10px;

&#x20;     touch-action: none;

&#x20;   }



&#x20;   .loading,

&#x20;   .error-box {

&#x20;     position: absolute;

&#x20;     inset: 0;

&#x20;     display: flex;

&#x20;     align-items: center;

&#x20;     justify-content: center;

&#x20;     padding: 25px;

&#x20;     text-align: center;

&#x20;     font-size: 11px;

&#x20;     font-weight: 800;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   .loading { color: var(--muted); pointer-events: none; }



&#x20;   .error-box {

&#x20;     display: none;

&#x20;     color: #ffd1d1;

&#x20;     background: rgba(13,24,32,.96);

&#x20;   }



&#x20;   .footer {

&#x20;     margin-top: 12px;

&#x20;     padding: 10px 12px;

&#x20;     color: #596b75;

&#x20;     font-size: 9px;

&#x20;     font-weight: 750;

&#x20;     letter-spacing: .13em;

&#x20;     text-align: center;

&#x20;     text-transform: uppercase;

&#x20;   }



&#x20;   @media (max-width: 900px) {

&#x20;     .page { width: min(100% - 18px, 1560px); margin-top: 9px; }

&#x20;     .topbar { grid-template-columns: 1fr; }

&#x20;     .holding-panel { border-left: 0; border-top: 1px solid var(--border); padding: 18px; }

&#x20;     .brand-panel { padding: 23px 20px 20px; }

&#x20;     h1 { font-size: clamp(38px, 10vw, 62px); }

&#x20;     .metrics { grid-template-columns: repeat(3, minmax(0, 1fr)); }

&#x20;     .chart-toolbar { align-items: flex-start; flex-direction: column; }

&#x20;     .data-info { text-align: left; white-space: normal; }

&#x20;     .chart-wrap { height: 345px; }

&#x20;   }



&#x20;   @media (max-width: 520px) {

&#x20;     .page { width: calc(100% - 12px); margin-top: 6px; }

&#x20;     .brand-panel { padding: 20px 15px 17px; }

&#x20;     h1 { font-size: clamp(34px, 13vw, 50px); line-height: .91; }

&#x20;     .brand-word { font-size: 9px; }

&#x20;     .holding-panel { padding: 15px; }

&#x20;     .card-header { padding: 16px 12px 0; }

&#x20;     .station-name { font-size: 19px; }

&#x20;     .metrics { grid-template-columns: repeat(2, minmax(0, 1fr)); gap: 7px; }

&#x20;     .metric:last-child { grid-column: 1 / -1; }

&#x20;     .chart-toolbar { padding-left: 12px; padding-right: 12px; }

&#x20;     .legend { gap: 10px 13px; }

&#x20;     .chart-wrap { height: 325px; padding-left: 4px; padding-right: 4px; }

&#x20;   }

&#x20; </style>

</head>

<body>

&#x20; <main class="page">

&#x20;   <header class="topbar">

&#x20;     <div class="brand-panel">

&#x20;       <h1>FEC HYDROTEST<br>LIVE DASHBOARD</h1>

&#x20;       <div class="brand-word">TechSmith</div>

&#x20;     </div>



&#x20;     <aside class="holding-panel" aria-label="Hydrotest holding period">

&#x20;       <div class="holding-heading"><span class="orange-dot"></span>Hydrotest Holding Period</div>



&#x20;       <div class="holding-row">

&#x20;         <span class="holding-label">Holding Time</span>

&#x20;         <strong class="holding-value" id="holdingTime">00:00:00</strong>

&#x20;       </div>

&#x20;       <div class="holding-row">

&#x20;         <span class="holding-label">Remaining Hrs</span>

&#x20;         <strong class="holding-value remaining" id="remainingTime">24:00:00</strong>

&#x20;       </div>



&#x20;       <div class="holding-dates">

&#x20;         <div class="date-block">

&#x20;           <span class="date-label">Start</span>

&#x20;           <span class="date-value">21:30 HRS<br>21/8/2026</span>

&#x20;         </div>

&#x20;         <div class="date-block">

&#x20;           <span class="date-label">Completion</span>

&#x20;           <span class="date-value">21:30 HRS<br>22/8/2026</span>

&#x20;         </div>

&#x20;       </div>



&#x20;       <div class="header-actions">

&#x20;         <div class="status-pill" id="globalStatus">Connecting to Google Sheets…</div>

&#x20;         <button class="refresh-button" id="refreshButton" type="button">Refresh Data</button>

&#x20;       </div>

&#x20;     </aside>

&#x20;   </header>



&#x20;   <!-- GPS -->

&#x20;   <section class="chart-card">

&#x20;     <div class="card-header">

&#x20;       <div class="station-title-block">

&#x20;         <h2 class="station-name">GPS</h2>

&#x20;         <div class="latest-data-status" id="gpsLatestData">Updated based on latest data: --</div>

&#x20;         <div class="station-subtitle">Launcher · Hydrotest pressure and temperature trend</div>

&#x20;       </div>



&#x20;       <div class="metrics">

&#x20;         <div class="metric dwt" id="gpsDwtMetric">

&#x20;           <span class="metric-label">DWT</span>

&#x20;           <span class="metric-value" id="gpsDwt">--</span>

&#x20;         </div>

&#x20;         <div class="metric digital" id="gpsDigitalMetric">

&#x20;           <span class="metric-label">Digital PG</span>

&#x20;           <span class="metric-value" id="gpsDigital">--</span>

&#x20;         </div>

&#x20;         <div class="metric recorder" id="gpsRecorderMetric">

&#x20;           <span class="metric-label">Pressure Recorder</span>

&#x20;           <span class="metric-value" id="gpsRecorder">--</span>

&#x20;         </div>

&#x20;         <div class="metric ambient">

&#x20;           <span class="metric-label">Ambient temp.</span>

&#x20;           <span class="metric-value" id="gpsAmbient">--</span>

&#x20;         </div>

&#x20;         <div class="metric water">

&#x20;           <span class="metric-label">Water temp.</span>

&#x20;           <span class="metric-value" id="gpsWater">--</span>

&#x20;         </div>

&#x20;       </div>

&#x20;     </div>



&#x20;     <div class="chart-toolbar">

&#x20;       <div class="legend">

&#x20;         <span class="legend-item" id="gpsDwtLegend"><span class="legend-line dwt"></span>DWT · Pressure</span>

&#x20;         <span class="legend-item" id="gpsDigitalLegend"><span class="legend-line digital"></span>Digital PG · Pressure</span>

&#x20;         <span class="legend-item" id="gpsRecorderLegend"><span class="legend-line recorder"></span>Pressure Recorder · Pressure</span>

&#x20;         <span class="legend-item"><span class="legend-line ambient"></span>Ambient Temperature</span>

&#x20;         <span class="legend-item"><span class="legend-line water"></span>Water Temperature</span>

&#x20;       </div>

&#x20;       <div class="data-info" id="gpsInfo">Waiting for data…</div>

&#x20;     </div>



&#x20;     <div class="chart-wrap">

&#x20;       <canvas id="gpsChart"></canvas>

&#x20;       <div class="loading" id="gpsLoading">Loading GPS data…</div>

&#x20;       <div class="error-box" id="gpsError"></div>

&#x20;     </div>

&#x20;   </section>



&#x20;   <!-- GPP4 -->

&#x20;   <section class="chart-card">

&#x20;     <div class="card-header">

&#x20;       <div class="station-title-block">

&#x20;         <h2 class="station-name">GPP4</h2>

&#x20;         <div class="latest-data-status" id="gpp4LatestData">Updated based on latest data: --</div>

&#x20;         <div class="station-subtitle">Receiver · Hydrotest pressure and temperature trend</div>

&#x20;       </div>



&#x20;       <div class="metrics">

&#x20;         <div class="metric dwt" id="gpp4DwtMetric">

&#x20;           <span class="metric-label">DWT</span>

&#x20;           <span class="metric-value" id="gpp4Dwt">--</span>

&#x20;         </div>

&#x20;         <div class="metric digital" id="gpp4DigitalMetric">

&#x20;           <span class="metric-label">Digital PG</span>

&#x20;           <span class="metric-value" id="gpp4Digital">--</span>

&#x20;         </div>

&#x20;         <div class="metric recorder" id="gpp4RecorderMetric">

&#x20;           <span class="metric-label">Pressure Recorder</span>

&#x20;           <span class="metric-value" id="gpp4Recorder">--</span>

&#x20;         </div>

&#x20;         <div class="metric ambient">

&#x20;           <span class="metric-label">Ambient temp.</span>

&#x20;           <span class="metric-value" id="gpp4Ambient">--</span>

&#x20;         </div>

&#x20;         <div class="metric water">

&#x20;           <span class="metric-label">Water temp.</span>

&#x20;           <span class="metric-value" id="gpp4Water">--</span>

&#x20;         </div>

&#x20;       </div>

&#x20;     </div>



&#x20;     <div class="chart-toolbar">

&#x20;       <div class="legend">

&#x20;         <span class="legend-item" id="gpp4DwtLegend"><span class="legend-line dwt"></span>DWT · Pressure</span>

&#x20;         <span class="legend-item" id="gpp4DigitalLegend"><span class="legend-line digital"></span>Digital PG · Pressure</span>

&#x20;         <span class="legend-item" id="gpp4RecorderLegend"><span class="legend-line recorder"></span>Pressure Recorder · Pressure</span>

&#x20;         <span class="legend-item"><span class="legend-line ambient"></span>Ambient Temperature</span>

&#x20;         <span class="legend-item"><span class="legend-line water"></span>Water Temperature</span>

&#x20;       </div>

&#x20;       <div class="data-info" id="gpp4Info">Waiting for data…</div>

&#x20;     </div>



&#x20;     <div class="chart-wrap">

&#x20;       <canvas id="gpp4Chart"></canvas>

&#x20;       <div class="loading" id="gpp4Loading">Loading GPP4 data…</div>

&#x20;       <div class="error-box" id="gpp4Error"></div>

&#x20;     </div>

&#x20;   </section>



&#x20;   <div class="footer">Fly TechSmith · Data refreshes automatically every 60 seconds</div>

&#x20; </main>



&#x20; <script>

&#x20;   /\* =========================================================

&#x20;      GOOGLE SHEET CONFIGURATION

&#x20;      =========================================================



&#x20;      The supplied links do not contain a gid, so gid: "0" is used.

&#x20;      If the required data is on another tab, open that tab in Google

&#x20;      Sheets and replace gid below with the number after #gid=.

&#x20;   \*/

&#x20;   const STATIONS = {

&#x20;     gps: {

&#x20;       name: "GPS",

&#x20;       spreadsheetId: "1OucgLhFiTqkeWiXJ0aI7j\_tMsu9lVnqTxSK8y2AMCn4",

&#x20;       gid: "0",

&#x20;       canvasId: "gpsChart",

&#x20;       loadingId: "gpsLoading",

&#x20;       errorId: "gpsError",

&#x20;       infoId: "gpsInfo",

&#x20;       latestDataId: "gpsLatestData",

&#x20;       dwtId: "gpsDwt",

&#x20;       digitalId: "gpsDigital",

&#x20;       recorderId: "gpsRecorder",

&#x20;       dwtMetricId: "gpsDwtMetric",

&#x20;       digitalMetricId: "gpsDigitalMetric",

&#x20;       recorderMetricId: "gpsRecorderMetric",

&#x20;       dwtLegendId: "gpsDwtLegend",

&#x20;       digitalLegendId: "gpsDigitalLegend",

&#x20;       recorderLegendId: "gpsRecorderLegend",

&#x20;       ambientId: "gpsAmbient",

&#x20;       waterId: "gpsWater"

&#x20;     },

&#x20;     gpp4: {

&#x20;       name: "GPP4",

&#x20;       spreadsheetId: "1MKLNtFUQT8GiiVmyoXSkQjw7oPF2z44MO8gdCIUo5t0",

&#x20;       gid: "0",

&#x20;       canvasId: "gpp4Chart",

&#x20;       loadingId: "gpp4Loading",

&#x20;       errorId: "gpp4Error",

&#x20;       infoId: "gpp4Info",

&#x20;       latestDataId: "gpp4LatestData",

&#x20;       dwtId: "gpp4Dwt",

&#x20;       digitalId: "gpp4Digital",

&#x20;       recorderId: "gpp4Recorder",

&#x20;       dwtMetricId: "gpp4DwtMetric",

&#x20;       digitalMetricId: "gpp4DigitalMetric",

&#x20;       recorderMetricId: "gpp4RecorderMetric",

&#x20;       dwtLegendId: "gpp4DwtLegend",

&#x20;       digitalLegendId: "gpp4DigitalLegend",

&#x20;       recorderLegendId: "gpp4RecorderLegend",

&#x20;       ambientId: "gpp4Ambient",

&#x20;       waterId: "gpp4Water"

&#x20;     }

&#x20;   };



&#x20;   const AUTO\_REFRESH\_MS = 60 \* 1000;

&#x20;   const X\_AXIS\_TICK\_MINUTES = 30;



&#x20;   // Hydrotest 24-hour holding period shown in the header.

&#x20;   // Fixed to Malaysia time (+08:00) so it remains correct regardless of browser locale.

&#x20;   const HOLD\_START = new Date("2026-08-21T21:30:00+08:00");

&#x20;   const HOLD\_END = new Date("2026-08-22T21:30:00+08:00");



&#x20;   /\*

&#x20;     Header auto-detection.

&#x20;     Add your exact Google Sheet header text here if needed.

&#x20;   \*/

&#x20;   const COLUMN\_ALIASES = {

&#x20;     date: \[

&#x20;       "date", "test date", "record date"

&#x20;     ],

&#x20;     time: \[

&#x20;       "time", "record time", "reading time", "test time", "timestamp",

&#x20;       "date time", "datetime", "date/time"

&#x20;     ],

&#x20;     dwt: \[

&#x20;       "dwt", "dwt reading", "dwt pressure", "dwt reading bar", "dwt bar"

&#x20;     ],

&#x20;     digital: \[

&#x20;       "digital pg", "digital pressure", "digital pressure gauge",

&#x20;       "digital pg bar", "digital gauge", "digital"

&#x20;     ],

&#x20;     recorder: \[

&#x20;       "pressure recorder", "pressure recorder bar", "pressure chart recorder",

&#x20;       "recorder pressure", "recorder"

&#x20;     ],

&#x20;     ambient: \[

&#x20;       "ambient temperature", "ambient temp", "ambient temperature c",

&#x20;       "ambient temp c", "temperature ambient", "ambient", "tra"

&#x20;     ],

&#x20;     water: \[

&#x20;       "water temperature", "water temp", "water temperature c",

&#x20;       "water temp c", "temperature water", "trw"

&#x20;     ]

&#x20;   };



&#x20;   class DualAxisTimeChart {

&#x20;     constructor(canvas, stationName) {

&#x20;       this.canvas = canvas;

&#x20;       this.ctx = canvas.getContext("2d");

&#x20;       this.stationName = stationName;

&#x20;       this.data = \[];

&#x20;       this.hoverIndex = -1;

&#x20;       this.bounds = null;

&#x20;       this.colors = this.readColors();



&#x20;       this.resizeObserver = new ResizeObserver(() => this.render());

&#x20;       this.resizeObserver.observe(canvas.parentElement);



&#x20;       canvas.addEventListener("mousemove", event => this.onPointerMove(event));

&#x20;       canvas.addEventListener("mouseleave", () => {

&#x20;         this.hoverIndex = -1;

&#x20;         this.render();

&#x20;       });

&#x20;       canvas.addEventListener("touchstart", event => this.onTouch(event), { passive: true });

&#x20;       canvas.addEventListener("touchmove", event => this.onTouch(event), { passive: true });

&#x20;     }



&#x20;     readColors() {

&#x20;       const styles = getComputedStyle(document.documentElement);

&#x20;       return {

&#x20;         text: styles.getPropertyValue("--text").trim(),

&#x20;         muted: styles.getPropertyValue("--muted").trim(),

&#x20;         grid: styles.getPropertyValue("--grid").trim(),

&#x20;         dwt: styles.getPropertyValue("--dwt").trim(),

&#x20;         digital: styles.getPropertyValue("--digital").trim(),

&#x20;         recorder: styles.getPropertyValue("--recorder").trim(),

&#x20;         ambient: styles.getPropertyValue("--ambient").trim(),

&#x20;         water: styles.getPropertyValue("--water").trim(),

&#x20;         panel: styles.getPropertyValue("--panel").trim()

&#x20;       };

&#x20;     }



&#x20;     setData(data) {

&#x20;       this.data = \[...data].sort((a, b) => a.time - b.time);

&#x20;       this.hoverIndex = -1;

&#x20;       this.render();

&#x20;     }



&#x20;     resizeCanvas() {

&#x20;       const rect = this.canvas.getBoundingClientRect();

&#x20;       const dpr = Math.max(1, window.devicePixelRatio || 1);

&#x20;       const displayWidth = Math.max(1, Math.floor(rect.width));

&#x20;       const displayHeight = Math.max(1, Math.floor(rect.height));



&#x20;       const targetWidth = Math.floor(displayWidth \* dpr);

&#x20;       const targetHeight = Math.floor(displayHeight \* dpr);



&#x20;       if (this.canvas.width !== targetWidth || this.canvas.height !== targetHeight) {

&#x20;         this.canvas.width = targetWidth;

&#x20;         this.canvas.height = targetHeight;

&#x20;       }



&#x20;       this.ctx.setTransform(dpr, 0, 0, dpr, 0, 0);

&#x20;       return { width: displayWidth, height: displayHeight };

&#x20;     }



&#x20;     render() {

&#x20;       const { width, height } = this.resizeCanvas();

&#x20;       const ctx = this.ctx;

&#x20;       ctx.clearRect(0, 0, width, height);



&#x20;       if (!this.data.length) {

&#x20;         this.bounds = null;

&#x20;         return;

&#x20;       }



&#x20;       const mobile = width < 600;

&#x20;       const margin = {

&#x20;         top: 20,

&#x20;         right: mobile ? 52 : 68,

&#x20;         bottom: mobile ? 48 : 52,

&#x20;         left: mobile ? 52 : 68

&#x20;       };



&#x20;       const plot = {

&#x20;         left: margin.left,

&#x20;         top: margin.top,

&#x20;         right: width - margin.right,

&#x20;         bottom: height - margin.bottom

&#x20;       };

&#x20;       plot.width = Math.max(1, plot.right - plot.left);

&#x20;       plot.height = Math.max(1, plot.bottom - plot.top);

&#x20;       this.bounds = plot;



&#x20;       const firstTime = this.data\[0].time.getTime();

&#x20;       const lastTime = this.data\[this.data.length - 1].time.getTime();

&#x20;       const safeLastTime = lastTime === firstTime ? firstTime + 30 \* 60 \* 1000 : lastTime;



&#x20;       const pressureValues = this.data

&#x20;         .flatMap(d => \[d.dwt, d.digital, d.recorder])

&#x20;         .filter(Number.isFinite);

&#x20;       const tempValues = this.data

&#x20;         .flatMap(d => \[d.ambient, d.water])

&#x20;         .filter(Number.isFinite);



&#x20;       const pressureScale = makeScale(pressureValues, { includeZero: false, minSpan: 5 });

&#x20;       const tempScale = makeScale(tempValues, { includeZero: false, minSpan: 2 });



&#x20;       const xForTime = date =>

&#x20;         plot.left + ((date.getTime() - firstTime) / (safeLastTime - firstTime)) \* plot.width;



&#x20;       const yForPressure = value =>

&#x20;         plot.bottom - ((value - pressureScale.min) / (pressureScale.max - pressureScale.min)) \* plot.height;



&#x20;       const yForTemp = value =>

&#x20;         plot.bottom - ((value - tempScale.min) / (tempScale.max - tempScale.min)) \* plot.height;



&#x20;       this.drawBackground(plot);

&#x20;       this.drawYGrid(plot, pressureScale, tempScale);

&#x20;       this.drawXAxis(plot, firstTime, safeLastTime, xForTime);

&#x20;       this.drawAxisTitles(plot, width, height);



&#x20;       this.drawSeries("dwt", this.colors.dwt, xForTime, yForPressure, 2.6);

&#x20;       this.drawSeries("digital", this.colors.digital, xForTime, yForPressure, 2.4);

&#x20;       this.drawSeries("recorder", this.colors.recorder, xForTime, yForPressure, 2.4);

&#x20;       this.drawSeries("ambient", this.colors.ambient, xForTime, yForTemp, 2.0);

&#x20;       this.drawSeries("water", this.colors.water, xForTime, yForTemp, 2.0);

&#x20;       this.drawPoints(xForTime, yForPressure, yForTemp);



&#x20;       if (this.hoverIndex >= 0 \&\& this.hoverIndex < this.data.length) {

&#x20;         this.drawTooltip(this.data\[this.hoverIndex], plot, width, height, xForTime, yForPressure, yForTemp);

&#x20;       }

&#x20;     }



&#x20;     drawBackground(plot) {

&#x20;       const ctx = this.ctx;

&#x20;       ctx.save();

&#x20;       ctx.fillStyle = "rgba(255,255,255,0.018)";

&#x20;       ctx.fillRect(plot.left, plot.top, plot.width, plot.height);

&#x20;       ctx.restore();

&#x20;     }



&#x20;     drawYGrid(plot, pressureScale, tempScale) {

&#x20;       const ctx = this.ctx;

&#x20;       const ticks = 5;



&#x20;       ctx.save();

&#x20;       ctx.font = "11px Inter, system-ui, sans-serif";

&#x20;       ctx.textBaseline = "middle";



&#x20;       for (let i = 0; i <= ticks; i++) {

&#x20;         const ratio = i / ticks;

&#x20;         const y = plot.bottom - ratio \* plot.height;

&#x20;         const pressureValue = pressureScale.min + ratio \* (pressureScale.max - pressureScale.min);

&#x20;         const tempValue = tempScale.min + ratio \* (tempScale.max - tempScale.min);



&#x20;         ctx.strokeStyle = this.colors.grid;

&#x20;         ctx.lineWidth = 1;

&#x20;         ctx.beginPath();

&#x20;         ctx.moveTo(plot.left, y);

&#x20;         ctx.lineTo(plot.right, y);

&#x20;         ctx.stroke();



&#x20;         ctx.fillStyle = this.colors.muted;

&#x20;         ctx.textAlign = "right";

&#x20;         ctx.fillText(formatAxisNumber(pressureValue), plot.left - 8, y);



&#x20;         ctx.textAlign = "left";

&#x20;         ctx.fillText(formatAxisNumber(tempValue), plot.right + 8, y);

&#x20;       }



&#x20;       ctx.restore();

&#x20;     }



&#x20;     drawXAxis(plot, firstTime, lastTime, xForTime) {

&#x20;       const ctx = this.ctx;

&#x20;       const stepMs = X\_AXIS\_TICK\_MINUTES \* 60 \* 1000;

&#x20;       let tick = ceilTime(firstTime, stepMs);

&#x20;       const maxLabels = Math.max(2, Math.floor(plot.width / 65));

&#x20;       const allTicks = \[];



&#x20;       while (tick <= lastTime + 1) {

&#x20;         allTicks.push(tick);

&#x20;         tick += stepMs;

&#x20;       }



&#x20;       if (!allTicks.length) {

&#x20;         allTicks.push(firstTime);

&#x20;       }



&#x20;       const skip = Math.max(1, Math.ceil(allTicks.length / maxLabels));



&#x20;       ctx.save();

&#x20;       ctx.font = "10px Inter, system-ui, sans-serif";

&#x20;       ctx.textAlign = "center";

&#x20;       ctx.textBaseline = "top";



&#x20;       allTicks.forEach((timeMs, index) => {

&#x20;         const x = xForTime(new Date(timeMs));



&#x20;         ctx.strokeStyle = "rgba(167,187,200,0.10)";

&#x20;         ctx.lineWidth = 1;

&#x20;         ctx.beginPath();

&#x20;         ctx.moveTo(x, plot.top);

&#x20;         ctx.lineTo(x, plot.bottom);

&#x20;         ctx.stroke();



&#x20;         ctx.strokeStyle = "rgba(167,187,200,0.30)";

&#x20;         ctx.beginPath();

&#x20;         ctx.moveTo(x, plot.bottom);

&#x20;         ctx.lineTo(x, plot.bottom + 5);

&#x20;         ctx.stroke();



&#x20;         if (index % skip === 0 || index === allTicks.length - 1) {

&#x20;           ctx.fillStyle = this.colors.muted;

&#x20;           ctx.fillText(formatTime(new Date(timeMs)), x, plot.bottom + 9);

&#x20;         }

&#x20;       });



&#x20;       ctx.strokeStyle = "rgba(167,187,200,0.30)";

&#x20;       ctx.beginPath();

&#x20;       ctx.moveTo(plot.left, plot.bottom);

&#x20;       ctx.lineTo(plot.right, plot.bottom);

&#x20;       ctx.stroke();



&#x20;       ctx.restore();

&#x20;     }



&#x20;     drawAxisTitles(plot, width, height) {

&#x20;       const ctx = this.ctx;

&#x20;       ctx.save();

&#x20;       ctx.font = "700 10px Inter, system-ui, sans-serif";

&#x20;       ctx.fillStyle = this.colors.muted;

&#x20;       ctx.textAlign = "center";



&#x20;       ctx.save();

&#x20;       ctx.translate(13, plot.top + plot.height / 2);

&#x20;       ctx.rotate(-Math.PI / 2);

&#x20;       ctx.fillText("PRESSURE (BARG)", 0, 0);

&#x20;       ctx.restore();



&#x20;       ctx.save();

&#x20;       ctx.translate(width - 12, plot.top + plot.height / 2);

&#x20;       ctx.rotate(Math.PI / 2);

&#x20;       ctx.fillText("TEMPERATURE (°C)", 0, 0);

&#x20;       ctx.restore();



&#x20;       ctx.fillText("TIME", plot.left + plot.width / 2, height - 7);

&#x20;       ctx.restore();

&#x20;     }



&#x20;     drawSeries(key, color, xForTime, yForValue, lineWidth) {

&#x20;       const ctx = this.ctx;

&#x20;       const valid = this.data.filter(d => Number.isFinite(d\[key]));

&#x20;       if (!valid.length) return;



&#x20;       ctx.save();

&#x20;       ctx.strokeStyle = color;

&#x20;       ctx.lineWidth = lineWidth;

&#x20;       ctx.lineJoin = "round";

&#x20;       ctx.lineCap = "round";

&#x20;       ctx.beginPath();



&#x20;       valid.forEach((d, index) => {

&#x20;         const x = xForTime(d.time);

&#x20;         const y = yForValue(d\[key]);

&#x20;         if (index === 0) ctx.moveTo(x, y);

&#x20;         else ctx.lineTo(x, y);

&#x20;       });



&#x20;       ctx.stroke();

&#x20;       ctx.restore();

&#x20;     }



&#x20;     drawPoints(xForTime, yForPressure, yForTemp) {

&#x20;       const ctx = this.ctx;

&#x20;       const draw = (key, color, yFunc) => {

&#x20;         ctx.save();

&#x20;         ctx.fillStyle = color;

&#x20;         for (const d of this.data) {

&#x20;           if (!Number.isFinite(d\[key])) continue;

&#x20;           const x = xForTime(d.time);

&#x20;           const y = yFunc(d\[key]);

&#x20;           ctx.beginPath();

&#x20;           ctx.arc(x, y, 2.3, 0, Math.PI \* 2);

&#x20;           ctx.fill();

&#x20;         }

&#x20;         ctx.restore();

&#x20;       };



&#x20;       draw("dwt", this.colors.dwt, yForPressure);

&#x20;       draw("digital", this.colors.digital, yForPressure);

&#x20;       draw("recorder", this.colors.recorder, yForPressure);

&#x20;       draw("ambient", this.colors.ambient, yForTemp);

&#x20;       draw("water", this.colors.water, yForTemp);

&#x20;     }



&#x20;     drawTooltip(row, plot, width, height, xForTime, yForPressure, yForTemp) {

&#x20;       const ctx = this.ctx;

&#x20;       const x = xForTime(row.time);



&#x20;       ctx.save();

&#x20;       ctx.strokeStyle = "rgba(255,255,255,0.30)";

&#x20;       ctx.lineWidth = 1;

&#x20;       ctx.setLineDash(\[4, 5]);

&#x20;       ctx.beginPath();

&#x20;       ctx.moveTo(x, plot.top);

&#x20;       ctx.lineTo(x, plot.bottom);

&#x20;       ctx.stroke();

&#x20;       ctx.setLineDash(\[]);



&#x20;       const values = \[

&#x20;         { label: "DWT", value: row.dwt, unit: " barg", color: this.colors.dwt },

&#x20;         { label: "Digital PG", value: row.digital, unit: " barg", color: this.colors.digital },

&#x20;         { label: "Pressure Recorder", value: row.recorder, unit: " barg", color: this.colors.recorder },

&#x20;         { label: "Ambient", value: row.ambient, unit: " °C", color: this.colors.ambient },

&#x20;         { label: "Water", value: row.water, unit: " °C", color: this.colors.water }

&#x20;       ].filter(v => Number.isFinite(v.value));



&#x20;       const lines = \[

&#x20;         formatDateTime(row.time, row.hasDate),

&#x20;         ...values.map(v => `${v.label}: ${Number.isFinite(v.value) ? formatValue(v.value) + v.unit : "--"}`)

&#x20;       ];



&#x20;       ctx.font = "12px Inter, system-ui, sans-serif";

&#x20;       const textWidth = Math.max(...lines.map(line => ctx.measureText(line).width));

&#x20;       const boxWidth = textWidth + 28;

&#x20;       const lineHeight = 20;

&#x20;       const boxHeight = lines.length \* lineHeight + 16;

&#x20;       let boxX = x + 12;

&#x20;       let boxY = plot.top + 10;



&#x20;       if (boxX + boxWidth > width - 6) boxX = x - boxWidth - 12;

&#x20;       if (boxY + boxHeight > height - 6) boxY = height - boxHeight - 6;

&#x20;       boxX = Math.max(6, boxX);

&#x20;       boxY = Math.max(6, boxY);



&#x20;       roundRect(ctx, boxX, boxY, boxWidth, boxHeight, 10);

&#x20;       ctx.fillStyle = "rgba(17,31,41,0.98)";

&#x20;       ctx.fill();

&#x20;       ctx.strokeStyle = "rgba(255,255,255,0.18)";

&#x20;       ctx.stroke();



&#x20;       lines.forEach((line, index) => {

&#x20;         const y = boxY + 14 + index \* lineHeight;

&#x20;         ctx.textBaseline = "top";

&#x20;         ctx.textAlign = "left";

&#x20;         ctx.font = index === 0

&#x20;           ? "700 12px Inter, system-ui, sans-serif"

&#x20;           : "12px Inter, system-ui, sans-serif";

&#x20;         ctx.fillStyle = index === 0 ? this.colors.text : this.colors.muted;

&#x20;         ctx.fillText(line, boxX + 14, y);

&#x20;       });



&#x20;       const pointData = \[

&#x20;         \[row.dwt, this.colors.dwt, yForPressure],

&#x20;         \[row.digital, this.colors.digital, yForPressure],

&#x20;         \[row.recorder, this.colors.recorder, yForPressure],

&#x20;         \[row.ambient, this.colors.ambient, yForTemp],

&#x20;         \[row.water, this.colors.water, yForTemp]

&#x20;       ];



&#x20;       for (const \[value, color, yFunc] of pointData) {

&#x20;         if (!Number.isFinite(value)) continue;

&#x20;         ctx.beginPath();

&#x20;         ctx.arc(x, yFunc(value), 5, 0, Math.PI \* 2);

&#x20;         ctx.fillStyle = color;

&#x20;         ctx.fill();

&#x20;         ctx.lineWidth = 2;

&#x20;         ctx.strokeStyle = this.colors.panel;

&#x20;         ctx.stroke();

&#x20;       }



&#x20;       ctx.restore();

&#x20;     }



&#x20;     onPointerMove(event) {

&#x20;       if (!this.bounds || !this.data.length) return;

&#x20;       const rect = this.canvas.getBoundingClientRect();

&#x20;       const x = event.clientX - rect.left;

&#x20;       this.setNearestHover(x);

&#x20;     }



&#x20;     onTouch(event) {

&#x20;       if (!this.bounds || !this.data.length || !event.touches.length) return;

&#x20;       const rect = this.canvas.getBoundingClientRect();

&#x20;       const x = event.touches\[0].clientX - rect.left;

&#x20;       this.setNearestHover(x);

&#x20;     }



&#x20;     setNearestHover(x) {

&#x20;       const plot = this.bounds;

&#x20;       if (x < plot.left || x > plot.right) {

&#x20;         if (this.hoverIndex !== -1) {

&#x20;           this.hoverIndex = -1;

&#x20;           this.render();

&#x20;         }

&#x20;         return;

&#x20;       }



&#x20;       const first = this.data\[0].time.getTime();

&#x20;       const last = this.data\[this.data.length - 1].time.getTime();

&#x20;       const target = first + ((x - plot.left) / plot.width) \* Math.max(1, last - first);



&#x20;       let nearest = 0;

&#x20;       let nearestDistance = Infinity;

&#x20;       this.data.forEach((d, index) => {

&#x20;         const distance = Math.abs(d.time.getTime() - target);

&#x20;         if (distance < nearestDistance) {

&#x20;           nearestDistance = distance;

&#x20;           nearest = index;

&#x20;         }

&#x20;       });



&#x20;       if (nearest !== this.hoverIndex) {

&#x20;         this.hoverIndex = nearest;

&#x20;         this.render();

&#x20;       }

&#x20;     }

&#x20;   }



&#x20;   const charts = {};



&#x20;   document.addEventListener("DOMContentLoaded", () => {

&#x20;     charts.gps = new DualAxisTimeChart(document.getElementById("gpsChart"), "GPS");

&#x20;     charts.gpp4 = new DualAxisTimeChart(document.getElementById("gpp4Chart"), "GPP4");



&#x20;     document.getElementById("refreshButton").addEventListener("click", () => refreshAll(true));



&#x20;     updateHoldingTimer();

&#x20;     setInterval(updateHoldingTimer, 1000);

&#x20;     refreshAll(false);

&#x20;     setInterval(() => refreshAll(false), AUTO\_REFRESH\_MS);

&#x20;   });



&#x20;   function updateHoldingTimer() {

&#x20;     const now = new Date();

&#x20;     const totalMs = Math.max(0, HOLD\_END - HOLD\_START);

&#x20;     const elapsedMs = Math.min(totalMs, Math.max(0, now - HOLD\_START));

&#x20;     const remainingMs = Math.max(0, HOLD\_END - now);



&#x20;     const holdingEl = document.getElementById("holdingTime");

&#x20;     const remainingEl = document.getElementById("remainingTime");

&#x20;     if (holdingEl) holdingEl.textContent = formatDuration(elapsedMs);

&#x20;     if (remainingEl) remainingEl.textContent = formatDuration(remainingMs);

&#x20;   }



&#x20;   function formatDuration(ms) {

&#x20;     const totalSeconds = Math.max(0, Math.floor(ms / 1000));

&#x20;     const hours = Math.floor(totalSeconds / 3600);

&#x20;     const minutes = Math.floor((totalSeconds % 3600) / 60);

&#x20;     const seconds = totalSeconds % 60;

&#x20;     return `${String(hours).padStart(2, "0")}:${String(minutes).padStart(2, "0")}:${String(seconds).padStart(2, "0")}`;

&#x20;   }



&#x20;   async function refreshAll(manual) {

&#x20;     const button = document.getElementById("refreshButton");

&#x20;     const globalStatus = document.getElementById("globalStatus");



&#x20;     if (manual) button.disabled = true;

&#x20;     globalStatus.textContent = "Updating data…";



&#x20;     const results = await Promise.allSettled(\[

&#x20;       loadStation("gps"),

&#x20;       loadStation("gpp4")

&#x20;     ]);



&#x20;     const successCount = results.filter(result => result.status === "fulfilled").length;

&#x20;     const now = new Date();



&#x20;     if (successCount === 2) {

&#x20;       globalStatus.textContent = `Live · updated ${formatTime(now)}`;

&#x20;     } else if (successCount === 1) {

&#x20;       globalStatus.textContent = `Partial data · ${formatTime(now)}`;

&#x20;     } else {

&#x20;       globalStatus.textContent = "Unable to load Google Sheets";

&#x20;     }



&#x20;     if (manual) button.disabled = false;

&#x20;   }



&#x20;   async function loadStation(key) {

&#x20;     const config = STATIONS\[key];

&#x20;     const loading = document.getElementById(config.loadingId);

&#x20;     const errorBox = document.getElementById(config.errorId);



&#x20;     loading.style.display = "flex";

&#x20;     errorBox.style.display = "none";

&#x20;     errorBox.textContent = "";



&#x20;     try {

&#x20;       const csvUrl =

&#x20;         `https://docs.google.com/spreadsheets/d/${config.spreadsheetId}/gviz/tq` +

&#x20;         `?tqx=out:csv\&gid=${encodeURIComponent(config.gid)}\&\_=${Date.now()}`;



&#x20;       const response = await fetch(csvUrl, { cache: "no-store" });

&#x20;       if (!response.ok) {

&#x20;         throw new Error(`Google Sheets returned HTTP ${response.status}.`);

&#x20;       }



&#x20;       const csvText = await response.text();

&#x20;       const table = parseCSV(csvText);

&#x20;       const parsed = tableToChartRows(table);



&#x20;       if (!parsed.rows.length) {

&#x20;         throw new Error(

&#x20;           `No usable readings found. Detected headers: ${parsed.headers.join(" | ") || "none"}`

&#x20;         );

&#x20;       }



&#x20;       charts\[key].setData(parsed.rows);

&#x20;       updateStationSummary(config, parsed.rows, parsed.columns, parsed.headers);



&#x20;       loading.style.display = "none";

&#x20;       return parsed.rows;

&#x20;     } catch (error) {

&#x20;       console.error(`${config.name} data error:`, error);

&#x20;       loading.style.display = "none";

&#x20;       errorBox.style.display = "flex";

&#x20;       errorBox.innerHTML =

&#x20;         `<div><strong>${escapeHtml(config.name)} data could not be loaded.</strong><br>` +

&#x20;         `${escapeHtml(error.message)}<br><br>` +

&#x20;         `Check that the Google Sheet is shared as <b>Anyone with the link – Viewer</b>, ` +

&#x20;         `the correct gid is configured, and the table contains Time, at least one pressure instrument column, Ambient Temperature and Water Temperature.</div>`;

&#x20;       throw error;

&#x20;     }

&#x20;   }



&#x20;   function updateStationSummary(config, rows, columns, headers) {

&#x20;     const latest = rows\[rows.length - 1];



&#x20;     updateInstrumentMetric(config.dwtId, config.dwtMetricId, config.dwtLegendId, rows, "dwt");

&#x20;     updateInstrumentMetric(config.digitalId, config.digitalMetricId, config.digitalLegendId, rows, "digital");

&#x20;     updateInstrumentMetric(config.recorderId, config.recorderMetricId, config.recorderLegendId, rows, "recorder");



&#x20;     document.getElementById(config.ambientId).textContent =

&#x20;       Number.isFinite(latest.ambient) ? `${formatValue(latest.ambient)} °C` : "--";

&#x20;     document.getElementById(config.waterId).textContent =

&#x20;       Number.isFinite(latest.water) ? `${formatValue(latest.water)} °C` : "--";



&#x20;     const first = rows\[0];

&#x20;     const last = rows\[rows.length - 1];



&#x20;     document.getElementById(config.latestDataId).textContent =

&#x20;       `Updated based on latest data: ${formatTime(last.time)} hrs`;



&#x20;     const rangeText = first.hasDate || last.hasDate

&#x20;       ? `${formatDateTime(first.time, true)} → ${formatDateTime(last.time, true)}`

&#x20;       : `${formatTime(first.time)} → ${formatTime(last.time)}`;



&#x20;     document.getElementById(config.infoId).textContent =

&#x20;       `${rows.length} readings · ${rangeText} · 30 min time grid`;

&#x20;   }



&#x20;   function updateInstrumentMetric(valueId, metricId, legendId, rows, key) {

&#x20;     const valueEl = document.getElementById(valueId);

&#x20;     const metricEl = document.getElementById(metricId);

&#x20;     const legendEl = document.getElementById(legendId);

&#x20;     const availableRows = rows.filter(row => Number.isFinite(row\[key]));

&#x20;     const available = availableRows.length > 0;



&#x20;     metricEl.style.display = available ? "block" : "none";

&#x20;     legendEl.classList.toggle("unavailable", !available);



&#x20;     if (available) {

&#x20;       const latestReading = availableRows\[availableRows.length - 1]\[key];

&#x20;       valueEl.textContent = `${formatValue(latestReading)} barg`;

&#x20;     } else {

&#x20;       valueEl.textContent = "--";

&#x20;     }

&#x20;   }



&#x20;   function tableToChartRows(table) {

&#x20;     if (!table.length) {

&#x20;       return { rows: \[], headers: \[], columns: {} };

&#x20;     }



&#x20;     const headerIndex = findHeaderRow(table);

&#x20;     if (headerIndex < 0) {

&#x20;       return { rows: \[], headers: table\[0] || \[], columns: {} };

&#x20;     }



&#x20;     const headers = table\[headerIndex].map(cell => String(cell || "").trim());

&#x20;     const columns = {

&#x20;       date: findColumn(headers, COLUMN\_ALIASES.date),

&#x20;       time: findColumn(headers, COLUMN\_ALIASES.time),

&#x20;       dwt: findColumn(headers, COLUMN\_ALIASES.dwt),

&#x20;       digital: findColumn(headers, COLUMN\_ALIASES.digital),

&#x20;       recorder: findColumn(headers, COLUMN\_ALIASES.recorder),

&#x20;       ambient: findColumn(headers, COLUMN\_ALIASES.ambient),

&#x20;       water: findColumn(headers, COLUMN\_ALIASES.water)

&#x20;     };



&#x20;     if (columns.time < 0 \&\& columns.date < 0) {

&#x20;       throw new Error(`Time column not found. Headers: ${headers.join(" | ")}`);

&#x20;     }

&#x20;     if (columns.dwt < 0 \&\& columns.digital < 0 \&\& columns.recorder < 0) {

&#x20;       throw new Error(`No DWT, Digital PG or Pressure Recorder column found. Headers: ${headers.join(" | ")}`);

&#x20;     }

&#x20;     if (columns.ambient < 0) {

&#x20;       throw new Error(`Ambient temperature column not found. Headers: ${headers.join(" | ")}`);

&#x20;     }

&#x20;     if (columns.water < 0) {

&#x20;       throw new Error(`Water temperature column not found. Headers: ${headers.join(" | ")}`);

&#x20;     }



&#x20;     const rawRows = table.slice(headerIndex + 1);

&#x20;     const rows = \[];

&#x20;     let rolloverDays = 0;

&#x20;     let previousMinutes = null;



&#x20;     for (const row of rawRows) {

&#x20;       if (isEmptyRow(row)) continue;



&#x20;       const dateText = columns.date >= 0 ? row\[columns.date] : "";

&#x20;       const timeText = columns.time >= 0 ? row\[columns.time] : "";

&#x20;       const parsedTime = parseDateAndTime(dateText, timeText);

&#x20;       if (!parsedTime) continue;



&#x20;       // When a sheet has only HH:mm / HH:mm:ss and crosses midnight,

&#x20;       // move the next readings to the following day automatically.

&#x20;       if (!parsedTime.hasDate) {

&#x20;         const minutes = parsedTime.date.getHours() \* 60 + parsedTime.date.getMinutes();

&#x20;         if (previousMinutes !== null \&\& minutes < previousMinutes - 360) {

&#x20;           rolloverDays += 1;

&#x20;         }

&#x20;         previousMinutes = minutes;

&#x20;         parsedTime.date.setDate(parsedTime.date.getDate() + rolloverDays);

&#x20;       }



&#x20;       const dwt = columns.dwt >= 0 ? parseNumeric(row\[columns.dwt]) : NaN;

&#x20;       const digital = columns.digital >= 0 ? parseNumeric(row\[columns.digital]) : NaN;

&#x20;       const recorder = columns.recorder >= 0 ? parseNumeric(row\[columns.recorder]) : NaN;

&#x20;       const ambient = parseNumeric(row\[columns.ambient]);

&#x20;       const water = parseNumeric(row\[columns.water]);



&#x20;       if (!\[dwt, digital, recorder, ambient, water].some(Number.isFinite)) continue;



&#x20;       rows.push({

&#x20;         time: parsedTime.date,

&#x20;         hasDate: parsedTime.hasDate,

&#x20;         dwt,

&#x20;         digital,

&#x20;         recorder,

&#x20;         ambient,

&#x20;         water

&#x20;       });

&#x20;     }



&#x20;     return { rows, headers, columns };

&#x20;   }



&#x20;   function findHeaderRow(table) {

&#x20;     const scanCount = Math.min(table.length, 20);

&#x20;     let bestIndex = -1;

&#x20;     let bestScore = -1;



&#x20;     for (let i = 0; i < scanCount; i++) {

&#x20;       const headers = table\[i].map(cell => String(cell || "").trim());

&#x20;       let score = 0;



&#x20;       if (findColumn(headers, COLUMN\_ALIASES.time) >= 0 || findColumn(headers, COLUMN\_ALIASES.date) >= 0) score += 2;

&#x20;       if (findColumn(headers, COLUMN\_ALIASES.dwt) >= 0) score += 2;

&#x20;       if (findColumn(headers, COLUMN\_ALIASES.digital) >= 0) score += 2;

&#x20;       if (findColumn(headers, COLUMN\_ALIASES.recorder) >= 0) score += 2;

&#x20;       if (findColumn(headers, COLUMN\_ALIASES.ambient) >= 0) score += 2;

&#x20;       if (findColumn(headers, COLUMN\_ALIASES.water) >= 0) score += 2;



&#x20;       if (score > bestScore) {

&#x20;         bestScore = score;

&#x20;         bestIndex = i;

&#x20;       }

&#x20;     }



&#x20;     return bestScore >= 6 ? bestIndex : -1;

&#x20;   }



&#x20;   function findColumn(headers, aliases) {

&#x20;     const normalizedHeaders = headers.map(normalizeHeader);

&#x20;     const normalizedAliases = aliases.map(normalizeHeader);



&#x20;     // Prefer exact matches.

&#x20;     for (const alias of normalizedAliases) {

&#x20;       const exact = normalizedHeaders.indexOf(alias);

&#x20;       if (exact >= 0) return exact;

&#x20;     }



&#x20;     // Then allow descriptive headers such as "Pipeline Pressure (barg)".

&#x20;     for (let i = 0; i < normalizedHeaders.length; i++) {

&#x20;       const header = normalizedHeaders\[i];

&#x20;       if (!header) continue;

&#x20;       for (const alias of normalizedAliases) {

&#x20;         if (alias.length >= 4 \&\& (header.includes(alias) || alias.includes(header))) {

&#x20;           return i;

&#x20;         }

&#x20;       }

&#x20;     }



&#x20;     return -1;

&#x20;   }



&#x20;   function normalizeHeader(value) {

&#x20;     return String(value || "")

&#x20;       .toLowerCase()

&#x20;       .replace(/°/g, "")

&#x20;       .replace(/\\(\[^)]\*\\)/g, " ")

&#x20;       .replace(/\[^a-z0-9]+/g, " ")

&#x20;       .replace(/\\s+/g, " ")

&#x20;       .trim();

&#x20;   }



&#x20;   function parseCSV(text) {

&#x20;     const rows = \[];

&#x20;     let row = \[];

&#x20;     let field = "";

&#x20;     let inQuotes = false;



&#x20;     for (let i = 0; i < text.length; i++) {

&#x20;       const char = text\[i];

&#x20;       const next = text\[i + 1];



&#x20;       if (char === '"') {

&#x20;         if (inQuotes \&\& next === '"') {

&#x20;           field += '"';

&#x20;           i++;

&#x20;         } else {

&#x20;           inQuotes = !inQuotes;

&#x20;         }

&#x20;       } else if (char === "," \&\& !inQuotes) {

&#x20;         row.push(field);

&#x20;         field = "";

&#x20;       } else if ((char === "\\n" || char === "\\r") \&\& !inQuotes) {

&#x20;         if (char === "\\r" \&\& next === "\\n") i++;

&#x20;         row.push(field);

&#x20;         rows.push(row);

&#x20;         row = \[];

&#x20;         field = "";

&#x20;       } else {

&#x20;         field += char;

&#x20;       }

&#x20;     }



&#x20;     if (field.length || row.length) {

&#x20;       row.push(field);

&#x20;       rows.push(row);

&#x20;     }



&#x20;     return rows;

&#x20;   }



&#x20;   function parseDateAndTime(dateValue, timeValue) {

&#x20;     const dateText = String(dateValue ?? "").trim();

&#x20;     const timeText = String(timeValue ?? "").trim();



&#x20;     // If the time/timestamp cell already contains a full date-time.

&#x20;     const timeAsFullDate = parseDateTimeString(timeText);

&#x20;     if (timeAsFullDate \&\& containsDateComponent(timeText)) {

&#x20;       return { date: timeAsFullDate, hasDate: true };

&#x20;     }



&#x20;     // Separate Date + Time columns.

&#x20;     if (dateText) {

&#x20;       const dateParts = parseDateOnly(dateText);

&#x20;       const timeParts = parseTimeOnly(timeText || "00:00:00");

&#x20;       if (dateParts \&\& timeParts) {

&#x20;         return {

&#x20;           date: new Date(

&#x20;             dateParts.year,

&#x20;             dateParts.month - 1,

&#x20;             dateParts.day,

&#x20;             timeParts.hour,

&#x20;             timeParts.minute,

&#x20;             timeParts.second

&#x20;           ),

&#x20;           hasDate: true

&#x20;         };

&#x20;       }

&#x20;     }



&#x20;     // Time-only sheet.

&#x20;     const onlyTime = parseTimeOnly(timeText || dateText);

&#x20;     if (onlyTime) {

&#x20;       return {

&#x20;         date: new Date(2000, 0, 1, onlyTime.hour, onlyTime.minute, onlyTime.second),

&#x20;         hasDate: false

&#x20;       };

&#x20;     }



&#x20;     // Last fallback for browser-readable date strings.

&#x20;     const fallback = parseDateTimeString(timeText || dateText);

&#x20;     if (fallback) {

&#x20;       return { date: fallback, hasDate: true };

&#x20;     }



&#x20;     return null;

&#x20;   }



&#x20;   function parseDateOnly(text) {

&#x20;     const clean = String(text).trim();



&#x20;     // D/M/YYYY, DD/MM/YYYY, D-M-YYYY

&#x20;     let match = clean.match(/^(\\d{1,2})\[\\/-](\\d{1,2})\[\\/-](\\d{2,4})$/);

&#x20;     if (match) {

&#x20;       let year = Number(match\[3]);

&#x20;       if (year < 100) year += 2000;

&#x20;       return { day: Number(match\[1]), month: Number(match\[2]), year };

&#x20;     }



&#x20;     // YYYY-MM-DD

&#x20;     match = clean.match(/^(\\d{4})-(\\d{1,2})-(\\d{1,2})$/);

&#x20;     if (match) {

&#x20;       return { year: Number(match\[1]), month: Number(match\[2]), day: Number(match\[3]) };

&#x20;     }



&#x20;     const date = new Date(clean);

&#x20;     if (!Number.isNaN(date.getTime())) {

&#x20;       return { day: date.getDate(), month: date.getMonth() + 1, year: date.getFullYear() };

&#x20;     }



&#x20;     return null;

&#x20;   }



&#x20;   function parseTimeOnly(text) {

&#x20;     const clean = String(text || "").trim().toLowerCase();

&#x20;     if (!clean) return null;



&#x20;     // 24-hour: 01:00, 01:00:00, 1300, 130000

&#x20;     let match = clean.match(/^(\\d{1,2}):(\\d{2})(?::(\\d{2}))?$/);

&#x20;     if (match) {

&#x20;       const hour = Number(match\[1]);

&#x20;       const minute = Number(match\[2]);

&#x20;       const second = Number(match\[3] || 0);

&#x20;       if (hour <= 23 \&\& minute <= 59 \&\& second <= 59) return { hour, minute, second };

&#x20;     }



&#x20;     match = clean.match(/^(\\d{1,2}):(\\d{2})(?::(\\d{2}))?\\s\*(am|pm)$/i);

&#x20;     if (match) {

&#x20;       let hour = Number(match\[1]);

&#x20;       const minute = Number(match\[2]);

&#x20;       const second = Number(match\[3] || 0);

&#x20;       const ampm = match\[4].toLowerCase();

&#x20;       if (hour === 12) hour = 0;

&#x20;       if (ampm === "pm") hour += 12;

&#x20;       return { hour, minute, second };

&#x20;     }



&#x20;     match = clean.match(/^(\\d{2})(\\d{2})(\\d{2})?$/);

&#x20;     if (match) {

&#x20;       const hour = Number(match\[1]);

&#x20;       const minute = Number(match\[2]);

&#x20;       const second = Number(match\[3] || 0);

&#x20;       if (hour <= 23 \&\& minute <= 59 \&\& second <= 59) return { hour, minute, second };

&#x20;     }



&#x20;     return null;

&#x20;   }



&#x20;   function parseDateTimeString(text) {

&#x20;     if (!text) return null;

&#x20;     const date = new Date(text);

&#x20;     return Number.isNaN(date.getTime()) ? null : date;

&#x20;   }



&#x20;   function containsDateComponent(text) {

&#x20;     const value = String(text || "");

&#x20;     return /\\d{1,4}\[\\/-]\\d{1,2}\[\\/-]\\d{1,4}/.test(value) || /\[A-Za-z]{3,}/.test(value);

&#x20;   }



&#x20;   function parseNumeric(value) {

&#x20;     if (value === null || value === undefined) return NaN;

&#x20;     const clean = String(value)

&#x20;       .replace(/,/g, "")

&#x20;       .replace(/\[^0-9.+\\-eE]/g, "")

&#x20;       .trim();

&#x20;     if (!clean) return NaN;

&#x20;     const number = Number(clean);

&#x20;     return Number.isFinite(number) ? number : NaN;

&#x20;   }



&#x20;   function isEmptyRow(row) {

&#x20;     return !row || row.every(cell => String(cell || "").trim() === "");

&#x20;   }



&#x20;   function makeScale(values, options = {}) {

&#x20;     if (!values.length) return { min: 0, max: 1 };



&#x20;     let min = Math.min(...values);

&#x20;     let max = Math.max(...values);



&#x20;     if (options.includeZero) min = Math.min(0, min);



&#x20;     const minSpan = options.minSpan || 1;

&#x20;     let span = max - min;

&#x20;     if (span < minSpan) {

&#x20;       const mid = (max + min) / 2;

&#x20;       min = mid - minSpan / 2;

&#x20;       max = mid + minSpan / 2;

&#x20;       span = minSpan;

&#x20;     }



&#x20;     const padding = Math.max(span \* 0.08, minSpan \* 0.08);

&#x20;     min -= padding;

&#x20;     max += padding;



&#x20;     return niceBounds(min, max);

&#x20;   }



&#x20;   function niceBounds(min, max) {

&#x20;     const range = niceNumber(max - min, false);

&#x20;     const step = niceNumber(range / 5, true);

&#x20;     return {

&#x20;       min: Math.floor(min / step) \* step,

&#x20;       max: Math.ceil(max / step) \* step

&#x20;     };

&#x20;   }



&#x20;   function niceNumber(range, round) {

&#x20;     const exponent = Math.floor(Math.log10(Math.max(range, Number.EPSILON)));

&#x20;     const fraction = range / Math.pow(10, exponent);

&#x20;     let niceFraction;



&#x20;     if (round) {

&#x20;       if (fraction < 1.5) niceFraction = 1;

&#x20;       else if (fraction < 3) niceFraction = 2;

&#x20;       else if (fraction < 7) niceFraction = 5;

&#x20;       else niceFraction = 10;

&#x20;     } else {

&#x20;       if (fraction <= 1) niceFraction = 1;

&#x20;       else if (fraction <= 2) niceFraction = 2;

&#x20;       else if (fraction <= 5) niceFraction = 5;

&#x20;       else niceFraction = 10;

&#x20;     }



&#x20;     return niceFraction \* Math.pow(10, exponent);

&#x20;   }



&#x20;   function ceilTime(timeMs, stepMs) {

&#x20;     return Math.ceil(timeMs / stepMs) \* stepMs;

&#x20;   }



&#x20;   function formatTime(date) {

&#x20;     return new Intl.DateTimeFormat("en-GB", {

&#x20;       hour: "2-digit",

&#x20;       minute: "2-digit",

&#x20;       hour12: false

&#x20;     }).format(date);

&#x20;   }



&#x20;   function formatDateTime(date, includeDate = true) {

&#x20;     if (!includeDate) return formatTime(date);

&#x20;     return new Intl.DateTimeFormat("en-GB", {

&#x20;       day: "2-digit",

&#x20;       month: "2-digit",

&#x20;       year: "numeric",

&#x20;       hour: "2-digit",

&#x20;       minute: "2-digit",

&#x20;       hour12: false

&#x20;     }).format(date);

&#x20;   }



&#x20;   function formatValue(value) {

&#x20;     if (!Number.isFinite(value)) return "--";

&#x20;     return Math.abs(value) >= 100 ? value.toFixed(1) : value.toFixed(2).replace(/0+$/, "").replace(/\\.$/, "");

&#x20;   }



&#x20;   function formatAxisNumber(value) {

&#x20;     if (Math.abs(value) >= 100) return value.toFixed(0);

&#x20;     if (Math.abs(value) >= 10) return value.toFixed(1).replace(/\\.0$/, "");

&#x20;     return value.toFixed(2).replace(/0+$/, "").replace(/\\.$/, "");

&#x20;   }



&#x20;   function roundRect(ctx, x, y, width, height, radius) {

&#x20;     const r = Math.min(radius, width / 2, height / 2);

&#x20;     ctx.beginPath();

&#x20;     ctx.moveTo(x + r, y);

&#x20;     ctx.arcTo(x + width, y, x + width, y + height, r);

&#x20;     ctx.arcTo(x + width, y + height, x, y + height, r);

&#x20;     ctx.arcTo(x, y + height, x, y, r);

&#x20;     ctx.arcTo(x, y, x + width, y, r);

&#x20;     ctx.closePath();

&#x20;   }



&#x20;   function escapeHtml(text) {

&#x20;     return String(text)

&#x20;       .replace(/\&/g, "\&amp;")

&#x20;       .replace(/</g, "\&lt;")

&#x20;       .replace(/>/g, "\&gt;")

&#x20;       .replace(/"/g, "\&quot;")

&#x20;       .replace(/'/g, "\&#039;");

&#x20;   }

&#x20; </script>

</body>

</html>

