# EV-Charging-station
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Hariom Malviya | EV Charging Station Management</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    background:#f4f7f9;
    color:#17212b;
}

/* HEADER */
header{
    background:#0b7a53;
    color:white;
    padding:18px 28px;
    display:flex;
    justify-content:space-between;
    align-items:center;
}

header h1{
    font-size:23px;
}

header span{
    font-size:14px;
}

/* LAYOUT */
.container{
    display:flex;
    min-height:calc(100vh - 66px);
}

/* SIDEBAR */
.sidebar{
    width:230px;
    background:#10251f;
    color:white;
    padding:20px 12px;
}

.sidebar h3{
    padding:10px 14px;
    margin-bottom:10px;
}

.sidebar button{
    width:100%;
    border:0;
    background:transparent;
    color:white;
    text-align:left;
    padding:13px 14px;
    border-radius:8px;
    margin:3px 0;
    cursor:pointer;
    font-size:15px;
}

.sidebar button:hover,
.sidebar button.active{
    background:#0b7a53;
}

/* MAIN */
main{
    flex:1;
    padding:25px;
    overflow:auto;
}

.page{
    display:none;
}

.page.active{
    display:block;
}

.title{
    margin-bottom:20px;
}

.title h2{
    font-size:25px;
}

.title p{
    color:#68737d;
    margin-top:5px;
}

/* CARDS */
.cards{
    display:grid;
    grid-template-columns:repeat(5,1fr);
    gap:15px;
    margin-bottom:25px;
}

.card{
    background:white;
    padding:20px;
    border-radius:12px;
    box-shadow:0 2px 10px #00000010;
}

.card small{
    color:#68737d;
}

.card h2{
    margin-top:9px;
    color:#0b7a53;
}

/* PANEL */
.panel{
    background:white;
    border-radius:12px;
    padding:20px;
    box-shadow:0 2px 10px #00000010;
    margin-bottom:20px;
}

.panel h3{
    margin-bottom:15px;
}

/* TABLE */
table{
    width:100%;
    border-collapse:collapse;
}

th,td{
    text-align:left;
    padding:12px;
    border-bottom:1px solid #e6e9eb;
    font-size:14px;
}

th{
    background:#f7f9fa;
}

/* STATUS */
.status{
    padding:5px 9px;
    border-radius:15px;
    font-size:12px;
    font-weight:bold;
}

.available{
    background:#dff7ea;
    color:#087443;
}

.charging{
    background:#fff0c7;
    color:#9a6500;
}

/* BUTTON */
.btn{
    border:0;
    padding:9px 13px;
    border-radius:7px;
    cursor:pointer;
    background:#0b7a53;
    color:white;
}

.btn:hover{
    background:#095f41;
}

/* FORM */
.form{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:15px;
}

label{
    font-size:13px;
    font-weight:bold;
    color:#4e5962;
}

input,select{
    width:100%;
    padding:11px;
    margin-top:6px;
    border:1px solid #ccd3d8;
    border-radius:7px;
}

.form-full{
    grid-column:1/-1;
}

/* MOBILE */
@media(max-width:900px){

    .cards{
        grid-template-columns:repeat(2,1fr);
    }

    .sidebar{
        width:180px;
    }
}

@media(max-width:600px){

    .container{
        display:block;
    }

    .sidebar{
        width:100%;
        display:flex;
        overflow:auto;
    }

    .sidebar h3{
        display:none;
    }

    .sidebar button{
        min-width:130px;
    }

    .cards{
        grid-template-columns:1fr;
    }

    .form{
        grid-template-columns:1fr;
    }

    main{
        padding:15px;
    }

    header{
        flex-direction:column;
        gap:8px;
        text-align:center;
    }
}
</style>
</head>

<body>

<!-- HEADER -->
<header>
    <h1>⚡ EV Charging Station Management System</h1>
    <span>Hariom Malviya | Admin Dashboard</span>
</header>

<div class="container">

<!-- SIDEBAR -->
<aside class="sidebar">

    <h3>MENU</h3>

    <button class="active"
        onclick="showPage('dashboard',this)">
        📊 Dashboard
    </button>

    <button onclick="showPage('stations',this)">
        🔋 Charging Stations
    </button>

    <button onclick="showPage('customers',this)">
        👤 Customers
    </button>

    <button onclick="showPage('sessions',this)">
        ⚡ Charging Sessions
    </button>

    <button onclick="showPage('payments',this)">
        💳 Payments
    </button>

    <button onclick="showPage('reports',this)">
        📈 Reports
    </button>

</aside>

<!-- MAIN CONTENT -->
<main>

<!-- DASHBOARD -->
<section id="dashboard" class="page active">

    <div class="title">
        <h2>Hariom Malviya Dashboard</h2>
        <p>Monitor your EV charging station in real time.</p>
    </div>

    <div class="cards">

        <div class="card">
            <small>Total Stations</small>
            <h2 id="totalStations">4</h2>
        </div>

        <div class="card">
            <small>Available Slots</small>
            <h2 id="availableSlots">2</h2>
        </div>

        <div class="card">
            <small>Charging Now</small>
            <h2 id="chargingNow">2</h2>
        </div>

        <div class="card">
            <small>Total Vehicles</small>
            <h2 id="totalVehicles">2</h2>
        </div>

        <div class="card">
            <small>Today's Revenue</small>
            <h2>₹1,850</h2>
        </div>

    </div>

    <div class="panel">

        <h3>Current Charging Status</h3>

        <table>

            <thead>
                <tr>
                    <th>Station</th>
                    <th>Slot</th>
                    <th>Vehicle No.</th>
                    <th>Progress</th>
                    <th>Status</th>
                </tr>
            </thead>

            <tbody id="dashTable"></tbody>

        </table>

    </div>

</section>


<!-- CHARGING STATIONS -->
<section id="stations" class="page">

    <div class="title">
        <h2>Charging Stations</h2>
        <p>View and manage all charging slots.</p>
    </div>

    <div class="panel">

        <table>

            <thead>
                <tr>
                    <th>Station</th>
                    <th>Slot</th>
                    <th>Power</th>
                    <th>Status</th>
                    <th>Action</th>
                </tr>
            </thead>

            <tbody id="stationTable"></tbody>

        </table>

    </div>

</section>


<!-- CUSTOMERS -->
<section id="customers" class="page">

    <div class="title">
        <h2>Customer Management</h2>
        <p>Add and manage customer details.</p>
    </div>

    <div class="panel">

        <div class="form">

            <div>
                <label>Customer Name</label>
                <input id="cname"
                       placeholder="Enter name">
            </div>

            <div>
                <label>Vehicle Number</label>
                <input id="vno"
                       placeholder="MP00AB1234">
            </div>

            <div>
                <label>Contact Number</label>
                <input id="phone"
                       placeholder="Enter mobile number">
            </div>

            <div>
                <label>Vehicle Type</label>

                <select id="vtype">
                    <option>Car</option>
                    <option>Bike</option>
                    <option>SUV</option>
                </select>
            </div>

            <div class="form-full">

                <button class="btn"
                        onclick="addCustomer()">
                    Add Customer
                </button>

            </div>

        </div>

    </div>


    <div class="panel">

        <table>

            <thead>
                <tr>
                    <th>Name</th>
                    <th>Vehicle No.</th>
                    <th>Contact</th>
                    <th>Vehicle</th>
                </tr>
            </thead>

            <tbody id="customerTable"></tbody>

        </table>

    </div>

</section>


<!-- SESSIONS -->
<section id="sessions" class="page">

    <div class="title">
        <h2>Charging Sessions</h2>
        <p>Start and stop charging sessions.</p>
    </div>

    <div class="panel">

        <div class="form">

            <div>
                <label>Customer Name</label>
                <input id="sname"
                       placeholder="Customer name">
            </div>

            <div>
                <label>Vehicle Number</label>
                <input id="svno"
                       placeholder="Vehicle number">
            </div>

            <div>
                <label>Units Consumed (kWh)</label>
                <input id="units"
                       type="number"
                       placeholder="0">
            </div>

            <div>
                <label>Rate per Unit</label>
                <input id="rate"
                       type="number"
                       value="15">
            </div>

            <div class="form-full">

                <button class="btn"
                        onclick="startSession()">
                    Start Charging
                </button>

            </div>

        </div>

    </div>


    <div class="panel">

        <table>

            <thead>
                <tr>
                    <th>Customer</th>
                    <th>Vehicle</th>
                    <th>Units</th>
                    <th>Amount</th>
                    <th>Status</th>
                </tr>
            </thead>

            <tbody id="sessionTable"></tbody>

        </table>

    </div>

</section>


<!-- PAYMENTS -->
<section id="payments" class="page">

    <div class="title">

        <h2>Payments</h2>

        <p>
            Payment history and transaction status.
        </p>

    </div>

    <div class="panel">

        <table>

            <thead>

                <tr>
                    <th>Transaction ID</th>
                    <th>Vehicle No.</th>
                    <th>Amount</th>
                    <th>Method</th>
                    <th>Status</th>
                </tr>

            </thead>

            <tbody>

                <tr>
                    <td>#EV1001</td>
                    <td>MP04AB1234</td>
                    <td>₹975</td>
                    <td>UPI</td>
                    <td>
                        <span class="status available">
                            Paid
                        </span>
                    </td>
                </tr>

                <tr>
                    <td>#EV1002</td>
                    <td>MP04CD5678</td>
                    <td>₹875</td>
                    <td>Card</td>
                    <td>
                        <span class="status available">
                            Paid
                        </span>
                    </td>
                </tr>

            </tbody>

        </table>

    </div>

</section>


<!-- REPORTS -->
<section id="reports" class="page">

    <div class="title">

        <h2>Reports</h2>

        <p>
            Charging station performance summary.
        </p>

    </div>

    <div class="cards">

        <div class="card">
            <small>Daily Sessions</small>
            <h2>18</h2>
        </div>

        <div class="card">
            <small>Units Consumed</small>
            <h2>124 kWh</h2>
        </div>

        <div class="card">
            <small>Monthly Revenue</small>
            <h2>₹42,650</h2>
        </div>

    </div>

    <div class="panel">

        <h3>Monthly Summary</h3>

        <p style="line-height:2">

            The station completed
            <b>356 charging sessions</b>
            this month with an estimated
            consumption of
            <b>2,480 kWh</b>.

        </p>

    </div>

</section>

</main>
</div>


<script>

/* STATION DATA */

let stations = [

    {
        name:"Station 1",
        slot:"A1",
        power:"60 kW",
        status:"Available",
        vehicle:"—",
        progress:"—"
    },

    {
        name:"Station 1",
        slot:"A2",
        power:"60 kW",
        status:"Charging",
        vehicle:"MP04AB1234",
        progress:"65%"
    },

    {
        name:"Station 2",
        slot:"B1",
        power:"120 kW",
        status:"Available",
        vehicle:"—",
        progress:"—"
    },

    {
        name:"Station 2",
        slot:"B2",
        power:"120 kW",
        status:"Charging",
        vehicle:"MP04CD5678",
        progress:"40%"
    }

];


/* CUSTOMER DATA */

let customers = [

    {
        name:"Rahul Sharma",
        vehicle:"MP04AB1234",
        phone:"9876543210",
        type:"Car"
    },

    {
        name:"Amit Verma",
        vehicle:"MP04CD5678",
        phone:"9123456780",
        type:"SUV"
    }

];


/* PAGE CHANGE */

function showPage(id,btn){

    document
    .querySelectorAll(".page")
    .forEach(page =>
        page.classList.remove("active")
    );

    document
    .getElementById(id)
    .classList.add("active");

    document
    .querySelectorAll(".sidebar button")
    .forEach(button =>
        button.classList.remove("active")
    );

    btn.classList.add("active");
}


/* STATUS BADGE */

function badge(status){

    return `
        <span class="status ${
            status === "Available"
            ? "available"
            : "charging"
        }">
            ${status}
        </span>
    `;
}


/* RENDER DATA */

function render(){

    /* DASHBOARD */

    dashTable.innerHTML =
        stations.map(station => `

            <tr>

                <td>${station.name}</td>

                <td>${station.slot}</td>

                <td>${station.vehicle}</td>

                <td>${station.progress}</td>

                <td>
                    ${badge(station.status)}
                </td>

            </tr>

        `).join("");


    /* STATIONS */

    stationTable.innerHTML =
        stations.map((station,index) => `

            <tr>

                <td>${station.name}</td>

                <td>${station.slot}</td>

                <td>${station.power}</td>

                <td>
                    ${badge(station.status)}
                </td>

                <td>

                    <button
                        class="btn"
                        onclick="toggleStation(${index})">

                        ${
                            station.status === "Charging"
                            ? "Stop"
                            : "Start"
                        }

                    </button>

                </td>

            </tr>

        `).join("");


    /* CUSTOMERS */

    customerTable.innerHTML =
        customers.map(customer => `

            <tr>

                <td>${customer.name}</td>

                <td>${customer.vehicle}</td>

                <td>${customer.phone}</td>

                <td>${customer.type}</td>

            </tr>

        `).join("");


    /* DASHBOARD COUNTERS */

    availableSlots.textContent =
        stations.filter(
            s => s.status === "Available"
        ).length;


    chargingNow.textContent =
        stations.filter(
            s => s.status === "Charging"
        ).length;


    totalVehicles.textContent =
        stations.filter(
            s => s.vehicle !== "—"
        ).length;

}


/* START / STOP STATION */

function toggleStation(index){

    let station = stations[index];

    if(station.status === "Charging"){

        station.status = "Available";
        station.vehicle = "—";
        station.progress = "—";

    }

    else{

        station.status = "Charging";
        station.vehicle =
            "DEMO-" + (1000 + index);

        station.progress = "0%";

    }

    render();
}


/* ADD CUSTOMER */

function addCustomer(){

    let name =
        document.getElementById("cname").value.trim();

    let vehicle =
        document.getElementById("vno").value.trim();

    let phone =
        document.getElementById("phone").value.trim();

    let type =
        document.getElementById("vtype").value;


    if(!name || !vehicle || !phone){

        alert("Please fill all fields");

        return;
    }


    customers.push({

        name:name,
        vehicle:vehicle,
        phone:phone,
        type:type

    });


    render();


    document.getElementById("cname").value="";
    document.getElementById("vno").value="";
    document.getElementById("phone").value="";


    alert("Customer added successfully!");

}


/* START SESSION */

function startSession(){

    let name =
        document.getElementById("sname").value.trim();

    let vehicle =
        document.getElementById("svno").value.trim();

    let units =
        Number(
            document.getElementById("units").value
        );

    let rate =
        Number(
            document.getElementById("rate").value
        );


    if(!name || !vehicle || !units){

        alert(
            "Please enter customer, vehicle and units"
        );

        return;
    }


    let amount = units * rate;


    document.getElementById("sessionTable")
    .innerHTML += `

        <tr>

            <td>${name}</td>

            <td>${vehicle}</td>

            <td>${units} kWh</td>

            <td>₹${amount}</td>

            <td>
                ${badge("Charging")}
            </td>

        </tr>

    `;


    alert("Charging session started!");

}


/* INITIAL LOAD */

render();

</script>

</body>
</html>