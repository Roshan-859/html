<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Brightloop | Subscription Management</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
      background: #f7f7f5;
      color: #292b33;
    }

    .layout {
      display: flex;
      min-height: 100vh;
    }

    aside {
      width: 235px;
      background: #fff;
      border-right: 1px solid #e8e8e5;
      padding: 28px 18px;
    }

    .logo {
      font-size: 22px;
      font-weight: 750;
      margin: 0 0 35px 8px;
      color: #5557a8;
    }

    .nav-label {
      font-size: 11px;
      color: #92939c;
      margin: 22px 8px 10px;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    nav button {
      display: block;
      width: 100%;
      border: 0;
      background: transparent;
      text-align: left;
      padding: 12px;
      margin: 3px 0;
      border-radius: 8px;
      color: #62636c;
      cursor: pointer;
      font-size: 14px;
    }

    nav button:hover,
    nav button.active {
      background: #eeeeff;
      color: #5557a8;
    }

    main {
      flex: 1;
      padding: 32px;
      min-width: 0;
    }

    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 15px;
      margin-bottom: 30px;
    }

    h1 {
      font-size: 27px;
      margin-bottom: 7px;
    }

    .subtitle {
      color: #81828b;
      font-size: 14px;
    }

    .button {
      background: #5557a8;
      color: white;
      border: none;
      padding: 11px 16px;
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
    }

    .metrics {
      display: grid;
      grid-template-columns: repeat(4, minmax(0, 1fr));
      gap: 16px;
      margin-bottom: 24px;
    }

    .card {
      background: white;
      border: 1px solid #eaeae7;
      border-radius: 12px;
      padding: 21px;
    }

    .metric-title {
      font-size: 13px;
      color: #81828b;
      margin-bottom: 15px;
    }

    .metric-value {
      font-size: 27px;
      font-weight: 700;
    }

    .metric-note {
      font-size: 12px;
      color: #628b70;
      margin-top: 9px;
    }

    .content-grid {
      display: grid;
      grid-template-columns: 1.5fr 1fr;
      gap: 20px;
      margin-bottom: 24px;
    }

    .section-title {
      font-size: 17px;
      margin-bottom: 18px;
    }

    .chart {
      height: 175px;
      display: flex;
      align-items: end;
      justify-content: space-around;
      gap: 12px;
      padding-top: 15px;
      border-bottom: 1px solid #eee;
    }

    .bar-group {
      height: 100%;
      flex: 1;
      display: flex;
      flex-direction: column;
      justify-content: end;
      align-items: center;
      gap: 8px;
      font-size: 11px;
      color: #85858d;
    }

    .bar {
      width: min(34px, 80%);
      background: #c7c8ee;
      border-radius: 6px 6px 0 0;
      min-height: 8px;
    }

    .bar.current {
      background: #5557a8;
    }

    .insight {
      padding: 14px;
      background: #f4f3ff;
      border-radius: 9px;
      margin-bottom: 12px;
      font-size: 13px;
      line-height: 1.6;
    }

    .insight strong {
      display: block;
      margin-bottom: 4px;
    }

    .table-card {
      overflow-x: auto;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      min-width: 600px;
    }

    th, td {
      text-align: left;
      padding: 15px 12px;
      border-bottom: 1px solid #f0f0ed;
      font-size: 13px;
    }

    th {
      color: #888991;
      font-weight: 500;
    }

    .status {
      display: inline-block;
      padding: 5px 9px;
      border-radius: 20px;
      font-size: 11px;
      background: #e2f3e7;
      color: #37794a;
    }

    .pending {
      background: #fff0d9;
      color: #9a6718;
    }

    .empty {
      padding: 35px;
      text-align: center;
      color: #85858d;
    }

    @media (max-width: 1000px) {
      .metrics {
        grid-template-columns: repeat(2, 1fr);
      }

      .content-grid {
        grid-template-columns: 1fr;
      }
    }

    @media (max-width: 650px) {
      .layout {
        display: block;
      }

      aside {
        width: 100%;
        padding: 15px;
        border-right: 0;
        border-bottom: 1px solid #e8e8e5;
      }

      .logo {
        margin-bottom: 12px;
      }

      nav {
        display: flex;
        gap: 5px;
        overflow-x: auto;
      }

      nav button {
        width: auto;
        white-space: nowrap;
      }

      .nav-label {
        display: none;
      }

      main {
        padding: 18px;
      }

      header {
        align-items: flex-start;
        flex-direction: column;
      }
    }
  </style>
</head>

<body>
<div class="layout">
  <aside>
    <div class="logo">brightloop.</div>
    <nav>
      <div class="nav-label">Workspace</div>
      <button class="active" data-page="Overview">▦ Overview</button>
      <button data-page="Customers">♙ Customers</button>
      <button data-page="Products">◇ Products & Plans</button>
      <button data-page="Subscriptions">↻ Subscriptions</button>
      <button data-page="Invoices">▤ Invoices</button>
      <button data-page="Payments">⇄ Payments</button>
      <button data-page="Reports">▥ Reports</button>
    </nav>
  </aside>

  <main>
    <header>
      <div>
        <h1 id="page-title">Overview</h1>
        <p class="subtitle">Your subscription business at a glance.</p>
      </div>
      <button class="button" id="primary-action">+ New Subscription</button>
    </header>

    <section id="dashboard">
      <div class="metrics">
        <div class="card">
          <div class="metric-title">Monthly Recurring Revenue</div>
          <div class="metric-value" id="mrr">₹0</div>
          <div class="metric-note">Calculated from active records</div>
        </div>

        <div class="card">
          <div class="metric-title">Active Subscriptions</div>
          <div class="metric-value" id="active-count">0</div>
          <div class="metric-note">Currently active</div>
        </div>

        <div class="card">
          <div class="metric-title">Customers</div>
          <div class="metric-value" id="customer-count">0</div>
          <div class="metric-note">Registered customers</div>
        </div>

        <div class="card">
          <div class="metric-title">Pending Invoices</div>
          <div class="metric-value" id="pending-count">0</div>
          <div class="metric-note">Awaiting payment</div>
        </div>
      </div>

      <div class="content-grid">
        <div class="card">
          <h2 class="section-title">Subscription Revenue</h2>
          <div class="chart" id="chart"></div>
        </div>

        <div class="card">
          <h2 class="section-title">Business Intelligence</h2>
          <div class="insight">
            <strong>Revenue Detective</strong>
            Review your subscription and payment records to understand revenue changes.
          </div>
          <div class="insight">
            <strong>Renewal Watch</strong>
            Identify subscriptions approaching their renewal dates.
          </div>
          <div class="insight">
            <strong>Invoice Monitor</strong>
            Review unpaid invoices and payment statuses.
          </div>
        </div>
      </div>

      <div class="card table-card">
        <h2 class="section-title">Recent Subscriptions</h2>
        <table>
          <thead>
            <tr>
              <th>Customer</th>
              <th>Plan</th>
              <th>Monthly Price</th>
              <th>Status</th>
            </tr>
          </thead>
          <tbody id="subscription-table"></tbody>
        </table>
      </div>
    </section>

    <section class="card" id="other-page" hidden>
      <h2 class="section-title" id="other-title"></h2>
      <p id="other-description" class="subtitle"></p>
      <div id="other-content"></div>
    </section>
  </main>
</div>

<script>
  // Sample data for demonstrating the frontend.
  // This version uses browser memory only, not a real backend.
  const subscriptions = [
    { customer: "Acme Technologies", plan: "Professional", price: 2500, status: "Active" },
    { customer: "Northstar Labs", plan: "Starter", price: 999, status: "Active" },
    { customer: "Willow Studios", plan: "Enterprise", price: 6500, status: "Active" },
    { customer: "Cedar Solutions", plan: "Professional", price: 2500, status: "Pending" }
  ];

  const invoices = [
    { customer: "Acme Technologies", amount: 2500, status: "Paid" },
    { customer: "Northstar Labs", amount: 999, status: "Pending" },
    { customer: "Willow Studios", amount: 6500, status: "Paid" },
    { customer: "Cedar Solutions", amount: 2500, status: "Pending" }
  ];

  const customers = [
    "Acme Technologies",
    "Northstar Labs",
    "Willow Studios",
    "Cedar Solutions"
  ];

  function money(amount) {
    return new Intl.NumberFormat("en-IN", {
      style: "currency",
      currency: "INR",
      maximumFractionDigits: 0
    }).format(amount);
  }

  function renderDashboard() {
    const active = subscriptions.filter(s => s.status === "Active");
    const pending = invoices.filter(i => i.status === "Pending");

    document.getElementById("mrr").textContent =
      money(active.reduce((sum, s) => sum + s.price, 0));

    document.getElementById("active-count").textContent = active.length;
    document.getElementById("customer-count").textContent = customers.length;
    document.getElementById("pending-count").textContent = pending.length;

    document.getElementById("subscription-table").innerHTML =
      subscriptions.map(s => `
        <tr>
          <td>${s.customer}</td>
          <td>${s.plan}</td>
          <td>${money(s.price)}</td>
          <td>
            <span class="status ${s.status === "Pending" ? "pending" : ""}">
              ${s.status}
            </span>
          </td>
        </tr>
      `).join("");

    const values = [42, 55, 48, 67, 60, 78];
    const months = ["May", "Jun", "Jul", "Aug", "Sep", "Oct"];

    document.getElementById("chart").innerHTML =
      values.map((value, index) => `
        <div class="bar-group">
          <div class="bar ${index === values.length - 1 ? "current" : ""}"
               style="height:${value}%"></div>
          <span>${months[index]}</span>
        </div>
      `).join("");
  }

  const descriptions = {
    Customers: "Manage customer accounts and contact details.",
    Products: "Organize products, subscription plans and pricing.",
    Subscriptions: "Track subscription statuses, dates and renewals.",
    Invoices: "Review invoices, amounts and payment statuses.",
    Payments: "Review payment records and payment outcomes.",
    Reports: "Explore subscription and billing performance."
  };

  function showPage(page) {
    document.getElementById("page-title").textContent = page;
    document.getElementById("dashboard").hidden = page !== "Overview";
    document.getElementById("other-page").hidden = page === "Overview";

    document.querySelectorAll("nav button").forEach(button => {
      button.classList.toggle("active", button.dataset.page === page);
    });

    const action = document.getElementById("primary-action");
    action.textContent = page === "Overview" ? "+ New Subscription" : "+ Add " + page.replace(/s$/, "");

    if (page === "Overview") return;

    document.getElementById("other-title").textContent = page;
    document.getElementById("other-description").textContent =
      descriptions[page] || "Manage your business records.";

    let rows = [];

    if (page === "Customers") {
      rows = customers.map(name => `<tr><td>${name}</td></tr>`);
    } else if (page === "Products") {
      rows = [...new Set(subscriptions.map(s => s.plan))]
        .map(plan => `<tr><td>${plan}</td></tr>`);
    } else if (page === "Subscriptions") {
      rows = subscriptions.map(s =>
        `<tr><td>${s.customer}</td><td>${s.plan}</td><td>${money(s.price)}</td><td>${s.status}</td></tr>`
      );
    } else if (page === "Invoices" || page === "Payments") {
      rows = invoices.map(i =>
        `<tr><td>${i.customer}</td><td>${money(i.amount)}</td><td>${i.status}</td></tr>`
      );
    } else if (page === "Reports") {
      rows = [
        `<tr><td>Active subscriptions</td><td>${subscriptions.filter(s => s.status === "Active").length}</td></tr>`,
        `<tr><td>Pending invoices</td><td>${invoices.filter(i => i.status === "Pending").length}</td></tr>`,
        `<tr><td>Monthly recurring revenue</td><td>${money(subscriptions.filter(s => s.status === "Active").reduce((sum, s) => sum + s.price, 0))}</td></tr>`
      ];
    }

    const headers = page === "Subscriptions"
      ? "<th>Customer</th><th>Plan</th><th>Price</th><th>Status</th>"
      : page === "Invoices" || page === "Payments"
        ? "<th>Customer</th><th>Amount</th><th>Status</th>"
        : page === "Reports"
          ? "<th>Metric</th><th>Value</th>"
          : "<th>Name</th>";

    document.getElementById("other-content").innerHTML = `
      <div style="overflow-x:auto;margin-top:24px">
        <table>
          <thead><tr>${headers}</tr></thead>
          <tbody>${rows.join("")}</tbody>
        </table>
      </div>
    `;
  }

  document.querySelectorAll("nav button").forEach(button => {
    button.addEventListener("click", () => showPage(button.dataset.page));
  });

  document.getElementById("primary-action").addEventListener("click", () => {
    alert("This is a frontend demonstration. A backend is required to save new records.");
  });

  renderDashboard();
</script>
</body>
</html>
