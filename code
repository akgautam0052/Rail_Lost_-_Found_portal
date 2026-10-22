<!DOCTYPE html>
<html lang="en" class="h-full bg-slate-50">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RailLost & Found - Indian Railways Official Retrieval Portal</title>
    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        ir: {
                            navy: '#002244',
                            navylight: '#003366',
                            gold: '#D4AF37',
                            goldhover: '#B59226',
                            red: '#B22222',
                            lightbg: '#F4F7FA'
                        }
                    },
                    fontFamily: {
                        sans: ['Inter', 'sans-serif']
                    }
                }
            }
        }
    </script>
    <style>
        .glass-panel {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
        }
        .custom-scrollbar::-webkit-scrollbar {
            width: 6px;
            height: 6px;
        }
        .custom-scrollbar::-webkit-scrollbar-track {
            background: #f1f1f1;
            border-radius: 4px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb {
            background: #cbd5e1;
            border-radius: 4px;
        }
        .custom-scrollbar::-webkit-scrollbar-thumb:hover {
            background: #94a3b8;
        }
    </style>
</head>
<body class="h-full flex flex-col font-sans text-slate-800 antialiased bg-slate-100">

    <!-- Top Emergency / Helpline Banner -->
    <div class="bg-ir-red text-white text-xs font-semibold py-1 px-4 text-center flex items-center justify-between shadow-inner">
        <div class="flex items-center space-x-2 container mx-auto justify-between">
            <span><i class="fa-solid fa-phone-volume mr-1.5 animate-pulse"></i> Railway Protection Force (RPF) Helpline: <strong class="underline">139</strong></span>
            <span class="hidden md:inline"><i class="fa-solid fa-shield-halved mr-1"></i> Official Passenger Property Recovery Portal</span>
            <span class="text-xs bg-white/20 px-2 py-0.5 rounded text-white">24x7 Assistance</span>
        </div>
    </div>

    <!-- Main Navigation Bar -->
    <header class="bg-ir-navy text-white sticky top-0 z-30 shadow-lg border-b-4 border-ir-gold">
        <div class="container mx-auto px-4 py-3 flex flex-wrap items-center justify-between gap-4">
            <!-- Brand Logo & Title -->
            <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('search-tab')">
                <div class="bg-ir-gold p-2.5 rounded-lg text-ir-navy shadow-md">
                    <i class="fa-solid fa-train-subway text-2xl"></i>
                </div>
                <div>
                    <div class="flex items-center space-x-2">
                        <h1 class="text-xl font-bold tracking-tight text-white leading-none">RailLost & Found</h1>
                        <span class="bg-ir-gold/20 text-ir-gold text-[10px] uppercase font-extrabold px-1.5 py-0.5 rounded border border-ir-gold/40">Portal</span>
                    </div>
                    <p class="text-xs text-slate-300 mt-1">Indian Railways Centralized Retrieval System</p>
                </div>
            </div>

            <!-- Global Quick Search Bar -->
            <div class="flex-1 max-w-md mx-2">
                <div class="relative">
                    <input type="text" id="globalSearchInput" placeholder="Quick Search by PNR, Train (12951), or Station..." 
                        class="w-full pl-10 pr-24 py-2 rounded-lg bg-ir-navylight text-white placeholder-slate-300 text-sm border border-slate-600 focus:outline-none focus:ring-2 focus:ring-ir-gold transition">
                    <i class="fa-solid fa-magnifying-glass absolute left-3 top-2.5 text-slate-400 text-sm"></i>
                    <button onclick="handleGlobalSearch()" class="absolute right-1 top-1 bottom-1 bg-ir-gold hover:bg-ir-goldhover text-ir-navy font-semibold px-3 text-xs rounded transition flex items-center">
                        Search
                    </button>
                </div>
            </div>

            <!-- RPF Emergency Quick Badge -->
            <div class="hidden lg:flex items-center space-x-3 text-xs bg-slate-800/80 p-2 rounded-lg border border-slate-700">
                <div class="w-8 h-8 rounded-full bg-emerald-500/20 text-emerald-400 flex items-center justify-center font-bold">
                    <i class="fa-solid fa-building-shield"></i>
                </div>
                <div>
                    <div class="text-slate-200 font-semibold">RPF Booth Sync</div>
                    <div class="text-emerald-400 text-[11px] flex items-center">
                        <span class="w-2 h-2 rounded-full bg-emerald-400 mr-1.5 animate-ping"></span> Live Station Network
                    </div>
                </div>
            </div>
        </div>

        <!-- Navigation Tabs -->
        <nav class="bg-ir-navylight/60 border-t border-slate-700/60 px-4">
            <div class="container mx-auto flex space-x-1 overflow-x-auto custom-scrollbar text-sm font-medium">
                <button id="nav-search-tab" onclick="switchTab('search-tab')" class="tab-btn px-4 py-3 border-b-2 border-ir-gold text-ir-gold font-semibold flex items-center space-x-2 whitespace-nowrap transition">
                    <i class="fa-solid fa-boxes-stacked"></i>
                    <span>Browse Found Items</span>
                    <span id="foundCountBadge" class="ml-1 bg-ir-gold/20 text-ir-gold text-xs px-2 py-0.5 rounded-full font-bold">0</span>
                </button>
                <button id="nav-report-tab" onclick="switchTab('report-tab')" class="tab-btn px-4 py-3 border-b-2 border-transparent text-slate-300 hover:text-white flex items-center space-x-2 whitespace-nowrap transition">
                    <i class="fa-solid fa-file-circle-plus"></i>
                    <span>Report Lost Item</span>
                </button>
                <button id="nav-match-tab" onclick="switchTab('match-tab')" class="tab-btn px-4 py-3 border-b-2 border-transparent text-slate-300 hover:text-white flex items-center space-x-2 whitespace-nowrap transition">
                    <i class="fa-solid fa-wand-magic-sparkles text-ir-gold"></i>
                    <span>AI Smart Match</span>
                    <span class="bg-emerald-500/20 text-emerald-300 text-[10px] px-1.5 py-0.5 rounded uppercase font-bold">Live</span>
                </button>
                <button id="nav-track-tab" onclick="switchTab('track-tab')" class="tab-btn px-4 py-3 border-b-2 border-transparent text-slate-300 hover:text-white flex items-center space-x-2 whitespace-nowrap transition">
                    <i class="fa-solid fa-route"></i>
                    <span>Track Claim / Report Status</span>
                </button>
            </div>
        </nav>
    </header>

    <!-- Main Dynamic Content Area -->
    <main class="flex-1 container mx-auto px-4 py-6">

        <!-- ================= SECTION 1: SEARCH & BROWSE FOUND ITEMS ================= -->
        <section id="search-tab" class="tab-content">
            <!-- Hero Stats & Welcome Banner -->
            <div class="bg-gradient-to-r from-ir-navy to-slate-800 text-white rounded-xl p-6 mb-6 shadow-md border border-slate-700 relative overflow-hidden">
                <div class="relative z-10 max-w-3xl">
                    <span class="bg-ir-gold text-ir-navy font-bold text-xs uppercase px-2.5 py-1 rounded-full inline-block mb-2">Central Railway Inventory</span>
                    <h2 class="text-2xl md:text-3xl font-extrabold tracking-tight">Found Articles Registry</h2>
                    <p class="text-slate-300 text-sm mt-1">Browse articles recovered by RPF officials, station staff, and fellow passengers across all major Indian Railway junctions.</p>
                </div>
                <div class="mt-4 grid grid-cols-2 sm:grid-cols-4 gap-3 text-center border-t border-slate-700/80 pt-4 text-xs">
                    <div class="bg-slate-900/40 p-2.5 rounded-lg border border-slate-700/50">
                        <div class="text-slate-400">Total Found Items</div>
                        <div id="statTotalFound" class="text-lg font-bold text-white">0</div>
                    </div>
                    <div class="bg-slate-900/40 p-2.5 rounded-lg border border-slate-700/50">
                        <div class="text-slate-400">Claimed & Returned</div>
                        <div id="statClaimed" class="text-lg font-bold text-emerald-400">0</div>
                    </div>
                    <div class="bg-slate-900/40 p-2.5 rounded-lg border border-slate-700/50">
                        <div class="text-slate-400">Stations Covered</div>
                        <div class="text-lg font-bold text-ir-gold">142+</div>
                    </div>
                    <div class="bg-slate-900/40 p-2.5 rounded-lg border border-slate-700/50">
                        <div class="text-slate-400">Active RPF Outposts</div>
                        <div class="text-lg font-bold text-sky-400">850+</div>
                    </div>
                </div>
            </div>

            <!-- Filters Bar -->
            <div class="bg-white rounded-xl p-4 shadow-sm border border-slate-200 mb-6">
                <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-5 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-500 mb-1">Search Keywords</label>
                        <input type="text" id="filterKeyword" oninput="applyFoundFilters()" placeholder="Item name, description..." 
                            class="w-full px-3 py-2 text-sm bg-slate-50 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-ir-navy">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-500 mb-1">Station / Location</label>
                        <select id="filterStation" onchange="applyFoundFilters()" class="w-full px-3 py-2 text-sm bg-slate-50 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-ir-navy">
                            <option value="">All Stations</option>
                            <option value="New Delhi Railway Station (NDLS)">New Delhi (NDLS)</option>
                            <option value="Mumbai Central (MMCT)">Mumbai Central (MMCT)</option>
                            <option value="Howrah Junction (HWH)">Howrah Junction (HWH)</option>
                            <option value="Chennai Central (MAS)">Chennai Central (MAS)</option>
                            <option value="Bengaluru City (SBC)">Bengaluru City (SBC)</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-500 mb-1">Item Category</label>
                        <select id="filterCategory" onchange="applyFoundFilters()" class="w-full px-3 py-2 text-sm bg-slate-50 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-ir-navy">
                            <option value="">All Categories</option>
                            <option value="Electronics">Electronics</option>
                            <option value="Luggage">Luggage & Bags</option>
                            <option value="Wallet/Documents">Wallet & Documents</option>
                            <option value="Jewellery">Jewellery & Valuables</option>
                            <option value="Clothing">Clothing</option>
                            <option value="Keys">Keys</option>
                            <option value="Other">Other</option>
                        </select>
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-500 mb-1">Status</label>
                        <select id="filterStatus" onchange="applyFoundFilters()" class="w-full px-3 py-2 text-sm bg-slate-50 border border-slate-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-ir-navy">
                            <option value="">All Statuses</option>
                            <option value="Unclaimed">Unclaimed at Booth</option>
                            <option value="Verification Pending">Claim Under Review</option>
                            <option value="Returned">Returned to Owner</option>
                        </select>
                    </div>
                    <div class="flex items-end">
                        <button onclick="resetFoundFilters()" class="w-full bg-slate-100 hover:bg-slate-200 text-slate-700 font-semibold py-2 px-3 text-sm rounded-lg transition border border-slate-300 flex items-center justify-center space-x-1">
                            <i class="fa-solid fa-rotate"></i>
                            <span>Reset Filters</span>
                        </button>
                    </div>
                </div>
            </div>

            <!-- Found Items Cards Grid -->
            <div id="foundItemsGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
                <!-- Dynamically populated by JS -->
            </div>

            <!-- Empty State Container -->
            <div id="noFoundResults" class="hidden bg-white rounded-xl p-10 text-center border border-slate-200 my-6">
                <i class="fa-solid fa-box-open text-4xl text-slate-300 mb-3"></i>
                <h3 class="text-lg font-bold text-slate-700">No Matching Found Items</h3>
                <p class="text-sm text-slate-500 mt-1 max-w-md mx-auto">We couldn't find any deposited items matching your search criteria. Try adjusting filters or submit a Lost Report.</p>
                <button onclick="switchTab('report-tab')" class="mt-4 bg-ir-navy hover:bg-ir-navylight text-white text-xs font-semibold px-4 py-2 rounded-lg transition">
                    Report a Lost Item Now
                </button>
            </div>
        </section>

        <!-- ================= SECTION 2: REPORT LOST ITEM FORM ================= -->
        <section id="report-tab" class="tab-content hidden">
            <div class="max-w-3xl mx-auto bg-white rounded-xl shadow-sm border border-slate-200 overflow-hidden">
                <div class="bg-ir-navy text-white p-5 border-b-4 border-ir-gold flex items-center justify-between">
                    <div>
                        <h2 class="text-xl font-bold flex items-center space-x-2">
                            <i class="fa-solid fa-file-pen text-ir-gold"></i>
                            <span>File Lost Article Complaint / Report</span>
                        </h2>
                        <p class="text-xs text-slate-300 mt-0.5">Report details to generate an official RPF tracking acknowledgement receipt.</p>
                    </div>
                    <span class="text-xs bg-slate-800 text-slate-300 px-3 py-1 rounded-full border border-slate-700">Official Form IR-88</span>
                </div>

                <form id="lostReportForm" onsubmit="handleLostReportSubmit(event)" class="p-6 space-y-6">
                    
                    <!-- Passenger Details -->
                    <div>
                        <h3 class="text-xs uppercase font-extrabold text-ir-navy tracking-wider mb-3 flex items-center">
                            <i class="fa-solid fa-user-check mr-2"></i> 1. Passenger Identification
                        </h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Full Name <span class="text-red-500">*</span></label>
                                <input type="text" required id="repName" placeholder="e.g. Rahul Sharma" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">PNR or Ticket Ref No. <span class="text-red-500">*</span></label>
                                <input type="text" required id="repPnr" placeholder="10-digit PNR (e.g. 2415893210)" pattern="[0-9]{10}" title="Please enter a valid 10-digit PNR" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Contact Phone Number <span class="text-red-500">*</span></label>
                                <input type="tel" required id="repPhone" placeholder="+91 9876543210" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Email Address <span class="text-red-500">*</span></label>
                                <input type="email" required id="repEmail" placeholder="passenger@email.com" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                        </div>
                    </div>

                    <hr class="border-slate-200">

                    <!-- Journey / Incident Details -->
                    <div>
                        <h3 class="text-xs uppercase font-extrabold text-ir-navy tracking-wider mb-3 flex items-center">
                            <i class="fa-solid fa-train-track mr-2"></i> 2. Journey & Location Details
                        </h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Train Number & Name <span class="text-red-500">*</span></label>
                                <input type="text" required id="repTrain" placeholder="e.g. 12951 - Rajdhani Express" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Station / Platform / Location <span class="text-red-500">*</span></label>
                                <input type="text" required id="repStation" placeholder="e.g. New Delhi Station / Platform 3" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Coach & Seat / Berth No. (If inside train)</label>
                                <input type="text" id="repCoachSeat" placeholder="e.g. Coach B4, Berth 22" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Date & Approx Time of Incident <span class="text-red-500">*</span></label>
                                <input type="datetime-local" required id="repDateTime" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                        </div>
                    </div>

                    <hr class="border-slate-200">

                    <!-- Item Characteristics -->
                    <div>
                        <h3 class="text-xs uppercase font-extrabold text-ir-navy tracking-wider mb-3 flex items-center">
                            <i class="fa-solid fa-box mr-2"></i> 3. Lost Article Details
                        </h3>
                        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Item Title / Headline <span class="text-red-500">*</span></label>
                                <input type="text" required id="repTitle" placeholder="e.g. Black Dell Inspiron Laptop Bag" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                            </div>
                            <div>
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Item Category <span class="text-red-500">*</span></label>
                                <select id="repCategory" required class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                                    <option value="">Select Category</option>
                                    <option value="Electronics">Electronics</option>
                                    <option value="Luggage">Luggage & Bags</option>
                                    <option value="Wallet/Documents">Wallet & Documents</option>
                                    <option value="Jewellery">Jewellery & Valuables</option>
                                    <option value="Clothing">Clothing</option>
                                    <option value="Keys">Keys</option>
                                    <option value="Other">Other</option>
                                </select>
                            </div>
                            <div class="sm:col-span-2">
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Detailed Description & Distinct Identifiers <span class="text-red-500">*</span></label>
                                <textarea required id="repDesc" rows="3" placeholder="Mention color, brand, unique scratches, serial numbers, keychains, or contents inside bag..." class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy"></textarea>
                            </div>
                            <div class="sm:col-span-2">
                                <label class="block text-xs font-semibold text-slate-700 mb-1">Upload Reference Photo / Invoice Copy (Optional Preview)</label>
                                <div class="flex items-center justify-center border-2 border-dashed border-slate-300 rounded-lg p-4 bg-slate-50 hover:bg-slate-100 transition cursor-pointer text-center relative" onclick="document.getElementById('repPhotoInput').click()">
                                    <input type="file" id="repPhotoInput" accept="image/*" class="hidden" onchange="previewImageUpload(this)">
                                    <div id="photoPreviewContainer" class="flex flex-col items-center">
                                        <i class="fa-solid fa-cloud-arrow-up text-2xl text-slate-400 mb-1"></i>
                                        <span class="text-xs text-slate-600 font-medium">Click to upload photo or drag and drop</span>
                                        <span class="text-[10px] text-slate-400">PNG, JPG or WEBP up to 5MB</span>
                                    </div>
                                    <img id="photoPreview" class="hidden max-h-32 rounded object-contain" alt="Preview">
                                </div>
                            </div>
                        </div>
                    </div>

                    <!-- Consent & Submit -->
                    <div class="pt-2 border-t border-slate-200 flex items-center justify-between">
                        <label class="flex items-center text-xs text-slate-600 cursor-pointer">
                            <input type="checkbox" required class="rounded border-slate-300 text-ir-navy focus:ring-ir-navy mr-2">
                            I certify that the information provided is accurate and true.
                        </label>
                        <button type="submit" class="bg-ir-navy hover:bg-ir-navylight text-white font-bold px-6 py-2.5 rounded-lg shadow-md hover:shadow-lg transition flex items-center space-x-2 text-sm">
                            <i class="fa-solid fa-paper-plane"></i>
                            <span>Submit Report</span>
                        </button>
                    </div>
                </form>
            </div>
        </section>

        <!-- ================= SECTION 3: AI SMART MATCH ENGINE ================= -->
        <section id="match-tab" class="tab-content hidden">
            <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6 mb-6">
                <div class="flex items-center justify-between mb-4 flex-wrap gap-2">
                    <div>
                        <h2 class="text-xl font-bold text-ir-navy flex items-center space-x-2">
                            <i class="fa-solid fa-wand-magic-sparkles text-ir-gold"></i>
                            <span>AI Smart Match Engine</span>
                        </h2>
                        <p class="text-xs text-slate-500">Cross-references reported lost articles with recently recovered RPF booth inventories using attribute comparison.</p>
                    </div>
                    <button onclick="runSmartMatch()" class="bg-ir-gold hover:bg-ir-goldhover text-ir-navy font-bold px-4 py-2 rounded-lg text-xs shadow transition flex items-center space-x-1">
                        <i class="fa-solid fa-rotate-right"></i>
                        <span>Re-Run AI Matching</span>
                    </button>
                </div>

                <div class="bg-amber-50 border border-amber-200 rounded-lg p-3 text-xs text-amber-800 mb-6 flex items-start space-x-2">
                    <i class="fa-solid fa-triangle-exclamation text-amber-600 mt-0.5 text-sm"></i>
                    <span><strong>Match Confidence Indicator:</strong> Match scores above 75% are highlighted for high correlation based on Category, Station, Train Number, and Keyword overlap. Select a match to immediately file a verified ownership claim.</span>
                </div>

                <!-- Matches Output Container -->
                <div id="smartMatchesContainer" class="space-y-4">
                    <!-- Dynamic rendering by JS -->
                </div>
            </div>
        </section>

        <!-- ================= SECTION 4: LOST ITEM STATUS TRACKER ================= -->
        <section id="track-tab" class="tab-content hidden">
            <div class="max-w-3xl mx-auto space-y-6">
                <!-- Search Box -->
                <div class="bg-white rounded-xl shadow-sm border border-slate-200 p-6">
                    <h2 class="text-xl font-bold text-ir-navy mb-1 flex items-center space-x-2">
                        <i class="fa-solid fa-route text-ir-gold"></i>
                        <span>Track Report / Claim Status</span>
                    </h2>
                    <p class="text-xs text-slate-500 mb-4">Enter your generated Report ID (e.g., <code class="bg-slate-100 text-ir-navy px-1.5 py-0.5 rounded font-mono">IR-LOST-2026-8841</code> or claim ID) to check live progress.</p>
                    
                    <div class="flex gap-2">
                        <input type="text" id="trackInput" placeholder="Enter ID e.g. IR-LOST-2026-8841" class="flex-1 px-4 py-2.5 border border-slate-300 rounded-lg text-sm font-mono focus:ring-2 focus:ring-ir-navy focus:outline-none">
                        <button onclick="trackStatus()" class="bg-ir-navy hover:bg-ir-navylight text-white font-semibold px-6 py-2.5 rounded-lg text-sm transition shadow flex items-center space-x-1">
                            <i class="fa-solid fa-magnifying-glass"></i>
                            <span>Track</span>
                        </button>
                    </div>
                </div>

                <!-- Timeline Display Area -->
                <div id="trackerResult" class="hidden bg-white rounded-xl shadow-sm border border-slate-200 p-6">
                    <!-- Dynamic rendering by JS -->
                </div>
            </div>
        </section>

    </main>

    <!-- Claim / Verification Modal -->
    <div id="claimModal" class="fixed inset-0 z-50 bg-slate-900/60 backdrop-blur-sm hidden flex items-center justify-center p-4">
        <div class="bg-white rounded-2xl max-w-lg w-full shadow-2xl overflow-hidden transform transition-all border border-slate-200">
            <div class="bg-ir-navy text-white px-6 py-4 flex justify-between items-center border-b-4 border-ir-gold">
                <div>
                    <h3 class="font-bold text-lg flex items-center space-x-2">
                        <i class="fa-solid fa-file-shield text-ir-gold"></i>
                        <span>Verify & Claim Item</span>
                    </h3>
                    <p class="text-xs text-slate-300">Submit ownership proof to RPF booth officer</p>
                </div>
                <button onclick="closeClaimModal()" class="text-slate-300 hover:text-white text-xl font-bold">&times;</button>
            </div>

            <form id="claimForm" onsubmit="handleClaimSubmit(event)" class="p-6 space-y-4">
                <input type="hidden" id="claimItemId">
                
                <div class="bg-slate-50 p-3 rounded-lg border border-slate-200 text-xs space-y-1">
                    <div class="font-semibold text-slate-700">Item Being Claimed:</div>
                    <div id="modalItemTitle" class="text-ir-navy font-bold text-sm"></div>
                    <div id="modalItemLocation" class="text-slate-500"></div>
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-700 mb-1">Claimant Full Name <span class="text-red-500">*</span></label>
                    <input type="text" id="claimName" required placeholder="Your full name as per Govt ID" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                </div>

                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">Contact Phone <span class="text-red-500">*</span></label>
                        <input type="tel" id="claimPhone" required placeholder="+91 9876543210" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-700 mb-1">PNR / Ticket No. <span class="text-red-500">*</span></label>
                        <input type="text" id="claimPnr" required placeholder="PNR number" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                    </div>
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-700 mb-1">Proof of Ownership / Specific Distinguishing Details <span class="text-red-500">*</span></label>
                    <textarea id="claimProof" required rows="3" placeholder="Describe specific inner contents, wallpaper, lock pin pattern, serial number, invoice details, or markings to prove ownership..." class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy"></textarea>
                </div>

                <div>
                    <label class="block text-xs font-semibold text-slate-700 mb-1">Govt ID Proof Type</label>
                    <select id="claimIdType" class="w-full px-3 py-2 text-sm border border-slate-300 rounded-lg focus:ring-2 focus:ring-ir-navy">
                        <option value="Aadhaar Card">Aadhaar Card</option>
                        <option value="PAN Card">PAN Card</option>
                        <option value="Driving License">Driving License</option>
                        <option value="Passport">Passport</option>
                    </select>
                </div>

                <div class="pt-3 border-t border-slate-200 flex justify-end space-x-2">
                    <button type="button" onclick="closeClaimModal()" class="px-4 py-2 text-xs font-semibold text-slate-600 hover:bg-slate-100 rounded-lg border border-slate-300 transition">Cancel</button>
                    <button type="submit" class="px-5 py-2 text-xs font-bold text-ir-navy bg-ir-gold hover:bg-ir-goldhover rounded-lg shadow transition flex items-center space-x-1">
                        <i class="fa-solid fa-check-circle"></i>
                        <span>Submit Claim Ticket</span>
                    </button>
                </div>
            </form>
        </div>
    </div>

    <!-- Toast Notification Popup Container -->
    <div id="toast" class="fixed bottom-5 right-5 z-50 transform translate-y-20 opacity-0 transition-all duration-300 ease-in-out bg-slate-900 text-white px-5 py-3 rounded-xl shadow-2xl flex items-center space-x-3 border-l-4 border-ir-gold">
        <i id="toastIcon" class="fa-solid fa-circle-check text-emerald-400 text-lg"></i>
        <div>
            <div id="toastTitle" class="font-bold text-sm">Action Successful</div>
            <div id="toastMessage" class="text-xs text-slate-300">Your details have been saved successfully.</div>
        </div>
    </div>

    <!-- Footer -->
    <footer class="bg-ir-navy text-slate-400 text-xs border-t-2 border-ir-gold mt-auto py-6">
        <div class="container mx-auto px-4 flex flex-col md:flex-row items-center justify-between gap-4 text-center md:text-left">
            <div class="flex items-center space-x-3">
                <div class="bg-ir-gold text-ir-navy p-1.5 rounded">
                    <i class="fa-solid fa-train text-base"></i>
                </div>
                <div>
                    <div class="text-white font-bold text-sm">RailLost & Found Portal</div>
                    <div>Ministry of Railways • RPF Passenger Welfare Division</div>
                </div>
            </div>
            <div class="text-slate-400 space-x-4">
                <a href="#" class="hover:text-ir-gold transition">RPF Guidelines</a>
                <span>•</span>
                <a href="#" class="hover:text-ir-gold transition">Station Contact Directory</a>
                <span>•</span>
                <a href="#" class="hover:text-ir-gold transition">Privacy Policy</a>
            </div>
            <div class="text-slate-500 text-[11px]">
                System Time: <span id="clock" class="font-mono text-slate-300">--:--:--</span>
            </div>
        </div>
    </footer>

    <!-- JavaScript Application Logic -->
    <script>
        // Default Sample Pre-populated Data for Indian Railways Found Directory
        const SAMPLE_FOUND_ITEMS = [
            {
                id: "IR-FOUND-1042",
                title: "Black Dell Laptop Bag",
                category: "Electronics",
                station: "New Delhi Railway Station (NDLS)",
                train: "12951 - Rajdhani Express",
                coachSeat: "Coach B4, Berth 22",
                dateFound: "2026-10-21",
                timeFound: "14:30",
                description: "Contains Dell 14-inch laptop, charger, black notebook, and blue water bottle.",
                rpfStation: "RPF Post Platform 1, NDLS",
                status: "Unclaimed",
                icon: "fa-laptop",
                tags: ["Dell", "Laptop", "Bag", "12951", "NDLS"]
            },
            {
                id: "IR-FOUND-1043",
                title: "Brown Leather Wallet with Aadhaar",
                category: "Wallet/Documents",
                station: "New Delhi Railway Station (NDLS)",
                train: "Platform 1 Waiting Bench",
                coachSeat: "N/A",
                dateFound: "2026-10-22",
                timeFound: "09:15",
                description: "WildHorn brown leather wallet. Contains Aadhaar Card under name 'R. Kumar', 2 SBI debit cards, cash.",
                rpfStation: "RPF Main Booth, NDLS",
                status: "Unclaimed",
                icon: "fa-wallet",
                tags: ["Wallet", "Aadhaar", "NDLS", "Cards"]
            },
            {
                id: "IR-FOUND-1044",
                title: "Blue Skybags Luggage Trolley",
                category: "Luggage",
                station: "Mumbai Central (MMCT)",
                train: "12002 - Shatabdi Express",
                coachSeat: "Coach C2, Overhead Rack",
                dateFound: "2026-10-20",
                timeFound: "21:10",
                description: "Medium sized blue hardcase trolley bag with red ribbon tied to top handle.",
                rpfStation: "RPF Station Officer, MMCT",
                status: "Verification Pending",
                icon: "fa-suitcase-rolling",
                tags: ["Luggage", "Skybags", "Shatabdi", "MMCT"]
            },
            {
                id: "IR-FOUND-1045",
                title: "Apple Watch Series 8 (Space Gray)",
                category: "Electronics",
                station: "Mumbai Central (MMCT)",
                train: "AC Executive Lounge",
                coachSeat: "Lounge Seat 14",
                dateFound: "2026-10-22",
                timeFound: "18:45",
                description: "Space gray watch with black sport band. Screen passcode protected.",
                rpfStation: "RPF Booth, MMCT Platform 3",
                status: "Unclaimed",
                icon: "fa-clock",
                tags: ["Apple", "Watch", "Smartwatch", "MMCT"]
            },
            {
                id: "IR-FOUND-1046",
                title: "Gold Ring in Red Velvet Pouch",
                category: "Jewellery",
                station: "Howrah Junction (HWH)",
                train: "12301 - Howrah Rajdhani",
                coachSeat: "Coach A1, Coupe B",
                dateFound: "2026-10-19",
                timeFound: "07:00",
                description: "Small red velvet pouch containing 1 ladies gold ring with floral design.",
                rpfStation: "RPF Inspector Office, HWH",
                status: "Unclaimed",
                icon: "fa-gem",
                tags: ["Gold", "Ring", "Jewellery", "Howrah", "12301"]
            },
            {
                id: "IR-FOUND-1047",
                title: "Bunch of Keys with Honda Keychain",
                category: "Keys",
                station: "Bengaluru City (SBC)",
                train: "Platform 4 Ticket Counter",
                coachSeat: "N/A",
                dateFound: "2026-10-22",
                timeFound: "11:20",
                description: "4 keys on a silver ring with a rubberized Honda bike logo keychain.",
                rpfStation: "RPF Helpdesk, SBC",
                status: "Returned",
                icon: "fa-key",
                tags: ["Keys", "Honda", "SBC"]
            }
        ];

        // Sample Pre-populated Reported Lost Items
        const SAMPLE_LOST_REPORTS = [
            {
                id: "IR-LOST-2026-8841",
                name: "Rahul Sharma",
                pnr: "2415893210",
                phone: "+91 9876543210",
                email: "rahul.s@example.com",
                train: "12951 - Rajdhani Express",
                station: "New Delhi Railway Station (NDLS)",
                coachSeat: "Coach B4, Seat 22",
                dateTime: "2026-10-21T14:00",
                title: "Black Dell Laptop Bag",
                category: "Electronics",
                description: "Black Dell laptop bag left in Coach B4, seat 22. Contains Dell laptop with sticker on back.",
                status: "Matching Found Items",
                statusStep: 3,
                timeline: [
                    { step: "Reported", time: "Oct 21, 2026 15:00", done: true },
                    { step: "RPF Notification Sent", time: "Oct 21, 2026 15:05", done: true },
                    { step: "Matching Found Item Located", time: "Oct 21, 2026 16:30", done: true },
                    { step: "Verification in Progress", time: "Pending Action", done: false },
                    { step: "Ready for Pickup at Booth", time: "-", done: false }
                ]
            }
        ];

        // Global State Manager initialized with LocalStorage fallback
        let foundItems = [];
        let lostReports = [];

        function initData() {
            const storedFound = localStorage.getItem('rail_found_items');
            if (storedFound) {
                foundItems = JSON.parse(storedFound);
            } else {
                foundItems = [...SAMPLE_FOUND_ITEMS];
                localStorage.setItem('rail_found_items', JSON.stringify(foundItems));
            }

            const storedLost = localStorage.getItem('rail_lost_reports');
            if (storedLost) {
                lostReports = JSON.parse(storedLost);
            } else {
                lostReports = [...SAMPLE_LOST_REPORTS];
                localStorage.setItem('rail_lost_reports', JSON.stringify(lostReports));
            }
        }

        // DOM Load Initializer
        document.addEventListener('DOMContentLoaded', () => {
            initData();
            renderFoundItems(foundItems);
            updateStats();
            runSmartMatch();
            startLiveClock();
        });

        // Tab Switching Logic
        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'));
            document.querySelectorAll('.tab-btn').forEach(btn => {
                btn.classList.remove('border-ir-gold', 'text-ir-gold', 'font-semibold');
                btn.classList.add('border-transparent', 'text-slate-300');
            });

            document.getElementById(tabId).classList.remove('hidden');
            const activeBtn = document.getElementById(`nav-${tabId}`);
            if (activeBtn) {
                activeBtn.classList.add('border-ir-gold', 'text-ir-gold', 'font-semibold');
                activeBtn.classList.remove('border-transparent', 'text-slate-300');
            }

            if(tabId === 'match-tab') {
                runSmartMatch();
            }
        }

        // Live Clock Tracker
        function startLiveClock() {
            setInterval(() => {
                const now = new Date();
                document.getElementById('clock').innerText = now.toLocaleTimeString('en-IN');
            }, 1000);
        }

        // Render Stats Badges
        function updateStats() {
            document.getElementById('foundCountBadge').innerText = foundItems.length;
            document.getElementById('statTotalFound').innerText = foundItems.length;
            
            const claimedCount = foundItems.filter(i => i.status === 'Returned' || i.status === 'Verification Pending').length;
            document.getElementById('statClaimed').innerText = claimedCount;
        }

        // Render Found Items Cards Grid
        function renderFoundItems(items) {
            const grid = document.getElementById('foundItemsGrid');
            const noResults = document.getElementById('noFoundResults');

            grid.innerHTML = '';

            if (items.length === 0) {
                noResults.classList.remove('hidden');
                return;
            } else {
                noResults.classList.add('hidden');
            }

            items.forEach(item => {
                let statusColor = 'bg-amber-100 text-amber-800 border-amber-300';
                if(item.status === 'Verification Pending') statusColor = 'bg-sky-100 text-sky-800 border-sky-300';
                if(item.status === 'Returned') statusColor = 'bg-emerald-100 text-emerald-800 border-emerald-300';

                const card = document.createElement('div');
                card.className = "bg-white rounded-xl shadow-sm border border-slate-200 hover:shadow-md transition flex flex-col justify-between overflow-hidden";
                card.innerHTML = `
                    <div>
                        <div class="p-4 border-b border-slate-100 bg-slate-50/50 flex items-start justify-between">
                            <div class="flex items-center space-x-3">
                                <div class="w-10 h-10 rounded-lg bg-ir-navy/10 text-ir-navy flex items-center justify-center font-bold text-lg">
                                    <i class="fa-solid ${item.icon || 'fa-box'}"></i>
                                </div>
                                <div>
                                    <span class="text-[10px] font-extrabold uppercase px-2 py-0.5 rounded bg-slate-200 text-slate-700">${item.category}</span>
                                    <h3 class="font-bold text-slate-800 text-base leading-snug mt-0.5">${escapeHtml(item.title)}</h3>
                                </div>
                            </div>
                        </div>
                        <div class="p-4 space-y-2 text-xs text-slate-600">
                            <div class="flex items-center space-x-2">
                                <i class="fa-solid fa-train text-ir-navy w-4 text-center"></i>
                                <span><strong>Train:</strong> ${escapeHtml(item.train)}</span>
                            </div>
                            <div class="flex items-center space-x-2">
                                <i class="fa-solid fa-location-dot text-ir-red w-4 text-center"></i>
                                <span><strong>Station:</strong> ${escapeHtml(item.station)}</span>
                            </div>
                            <div class="flex items-center space-x-2">
                                <i class="fa-solid fa-calendar-day text-slate-400 w-4 text-center"></i>
                                <span><strong>Deposited:</strong> ${item.dateFound} (${item.timeFound})</span>
                            </div>
                            <div class="flex items-center space-x-2">
                                <i class="fa-solid fa-building-shield text-slate-400 w-4 text-center"></i>
                                <span><strong>Booth:</strong> ${escapeHtml(item.rpfStation)}</span>
                            </div>
                            <p class="text-slate-500 pt-2 border-t border-slate-100 line-clamp-2">
                                ${escapeHtml(item.description)}
                            </p>
                        </div>
                    </div>
                    <div class="p-4 pt-0 mt-2 flex items-center justify-between border-t border-slate-100 pt-3">
                        <span class="text-[11px] font-semibold px-2.5 py-1 rounded-full border ${statusColor}">
                            ${item.status}
                        </span>
                        <button onclick="openClaimModal('${item.id}')" ${item.status === 'Returned' ? 'disabled' : ''} 
                            class="bg-ir-gold hover:bg-ir-goldhover text-ir-navy font-bold text-xs px-3.5 py-1.5 rounded-lg shadow-sm transition disabled:opacity-50 disabled:cursor-not-allowed flex items-center space-x-1">
                            <i class="fa-solid fa-hand-holding-hand"></i>
                            <span>${item.status === 'Returned' ? 'Claimed' : 'Claim Article'}</span>
                        </button>
                    </div>
                `;
                grid.appendChild(card);
            });
        }

        // Apply Filters on Found Items
        function applyFoundFilters() {
            const kw = document.getElementById('filterKeyword').value.toLowerCase().trim();
            const station = document.getElementById('filterStation').value;
            const category = document.getElementById('filterCategory').value;
            const status = document.getElementById('filterStatus').value;

            const filtered = foundItems.filter(item => {
                const matchKw = !kw || item.title.toLowerCase().includes(kw) || 
                                      item.description.toLowerCase().includes(kw) || 
                                      item.train.toLowerCase().includes(kw) || 
                                      item.id.toLowerCase().includes(kw);
                const matchStation = !station || item.station === station;
                const matchCategory = !category || item.category === category;
                const matchStatus = !status || item.status === status;

                return matchKw && matchStation && matchCategory && matchStatus;
            });

            renderFoundItems(filtered);
        }

        function resetFoundFilters() {
            document.getElementById('filterKeyword').value = '';
            document.getElementById('filterStation').value = '';
            document.getElementById('filterCategory').value = '';
            document.getElementById('filterStatus').value = '';
            renderFoundItems(foundItems);
        }

        // Handle Global Search Bar
        function handleGlobalSearch() {
            const query = document.getElementById('globalSearchInput').value.trim();
            if (!query) return;
            switchTab('search-tab');
            document.getElementById('filterKeyword').value = query;
            applyFoundFilters();
        }

        // Image Preview Handler
        function previewImageUpload(input) {
            const file = input.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const preview = document.getElementById('photoPreview');
                    const container = document.getElementById('photoPreviewContainer');
                    preview.src = e.target.result;
                    preview.classList.remove('hidden');
                    container.classList.add('hidden');
                }
                reader.readAsDataURL(file);
            }
        }

        // Handle Lost Item Submission
        function handleLostReportSubmit(e) {
            e.preventDefault();

            const newId = `IR-LOST-${new Date().getFullYear()}-${Math.floor(1000 + Math.random() * 9000)}`;
            
            const newReport = {
                id: newId,
                name: document.getElementById('repName').value,
                pnr: document.getElementById('repPnr').value,
                phone: document.getElementById('repPhone').value,
                email: document.getElementById('repEmail').value,
                train: document.getElementById('repTrain').value,
                station: document.getElementById('repStation').value,
                coachSeat: document.getElementById('repCoachSeat').value || 'N/A',
                dateTime: document.getElementById('repDateTime').value,
                title: document.getElementById('repTitle').value,
                category: document.getElementById('repCategory').value,
                description: document.getElementById('repDesc').value,
                status: "Reported",
                statusStep: 1,
                timeline: [
                    { step: "Report Filed", time: new Date().toLocaleString('en-IN'), done: true },
                    { step: "RPF Station Notification", time: "Dispatched to RPF Control", done: true },
                    { step: "Smart AI Inventory Matching", time: "In Progress", done: false },
                    { step: "Physical Verification", time: "Pending", done: false },
                    { step: "Ready for Pickup", time: "-", done: false }
                ]
            };

            lostReports.unshift(newReport);
            localStorage.setItem('rail_lost_reports', JSON.stringify(lostReports));

            document.getElementById('lostReportForm').reset();
            document.getElementById('photoPreview').classList.add('hidden');
            document.getElementById('photoPreviewContainer').classList.remove('hidden');

            showToast("Report Submitted Successfully!", `Your Tracking ID is ${newId}. Save this ID for lookup.`);
            
            // Switch to tracking tab with auto fill
            setTimeout(() => {
                switchTab('track-tab');
                document.getElementById('trackInput').value = newId;
                trackStatus();
            }, 1200);
        }

        // AI Smart Matching Engine Simulation
        function runSmartMatch() {
            const container = document.getElementById('smartMatchesContainer');
            container.innerHTML = '';

            if (lostReports.length === 0) {
                container.innerHTML = `
                    <div class="text-center py-8 text-slate-500 text-xs">
                        No active lost reports found to compare. Please submit a lost report first.
                    </div>
                `;
                return;
            }

            lostReports.forEach(report => {
                let highestMatch = null;
                let topScore = 0;

                foundItems.forEach(found => {
                    let score = 0;

                    // Match Category (30 pts)
                    if (found.category === report.category) score += 35;

                    // Match Station (25 pts)
                    if (found.station.toLowerCase().includes(report.station.toLowerCase()) || 
                        report.station.toLowerCase().includes(found.station.toLowerCase())) {
                        score += 30;
                    }

                    // Match Train Number (25 pts)
                    const reportTrainNo = report.train.match(/\d+/);
                    const foundTrainNo = found.train.match(/\d+/);
                    if (reportTrainNo && foundTrainNo && reportTrainNo[0] === foundTrainNo[0]) {
                        score += 25;
                    }

                    // Text Keyword overlap (10 pts)
                    const titleWords = report.title.toLowerCase().split(' ');
                    titleWords.forEach(w => {
                        if (w.length > 3 && found.description.toLowerCase().includes(w)) {
                            score += 5;
                        }
                    });

                    if (score > topScore) {
                        topScore = score;
                        highestMatch = found;
                    }
                });

                // Display Match Box
                const matchCard = document.createElement('div');
                matchCard.className = "border border-slate-200 rounded-xl p-4 bg-slate-50 hover:bg-white transition shadow-sm";

                const matchPercentage = Math.min(topScore, 98); // Cap realistic match percentage

                let scoreColor = 'bg-slate-200 text-slate-700';
                if (matchPercentage >= 75) scoreColor = 'bg-emerald-500 text-white';
                else if (matchPercentage >= 40) scoreColor = 'bg-amber-500 text-white';

                matchCard.innerHTML = `
                    <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 border-b border-slate-200 pb-3 mb-3">
                        <div>
                            <span class="text-[10px] font-mono text-slate-400">Report ID: ${report.id}</span>
                            <h3 class="font-bold text-ir-navy text-base">${escapeHtml(report.title)}</h3>
                            <p class="text-xs text-slate-500">Reported by ${escapeHtml(report.name)} • ${escapeHtml(report.station)}</p>
                        </div>
                        <div class="flex items-center space-x-3">
                            <div class="text-right">
                                <div class="text-[10px] uppercase font-bold text-slate-400">AI Confidence Score</div>
                                <div class="text-lg font-extrabold ${matchPercentage >= 75 ? 'text-emerald-600' : 'text-slate-700'}">${matchPercentage}% Match</div>
                            </div>
                            <span class="px-3 py-1.5 rounded-full font-bold text-xs shadow-sm ${scoreColor}">
                                ${matchPercentage}% Match
                            </span>
                        </div>
                    </div>

                    ${highestMatch ? `
                        <div class="bg-white rounded-lg p-3 border border-slate-200 text-xs grid grid-cols-1 md:grid-cols-3 gap-3 items-center">
                            <div class="md:col-span-2">
                                <div class="text-[10px] uppercase font-bold text-slate-400">Matched Deposited Item</div>
                                <div class="font-bold text-slate-800">${escapeHtml(highestMatch.title)} (${highestMatch.id})</div>
                                <div class="text-slate-500 mt-0.5">Found at: ${escapeHtml(highestMatch.station)} • ${escapeHtml(highestMatch.rpfStation)}</div>
                                <div class="text-slate-600 italic mt-1 bg-slate-50 p-2 rounded border border-slate-100">"${escapeHtml(highestMatch.description)}"</div>
                            </div>
                            <div class="flex flex-col justify-center items-end border-t md:border-t-0 md:border-l border-slate-200 pt-2 md:pt-0 md:pl-3 space-y-2">
                                <button onclick="openClaimModal('${highestMatch.id}')" class="w-full bg-ir-gold hover:bg-ir-goldhover text-ir-navy font-bold py-2 px-3 rounded-lg text-xs transition shadow flex items-center justify-center space-x-1">
                                    <i class="fa-solid fa-hand-holding-hand"></i>
                                    <span>Claim Match Now</span>
                                </button>
                                <button onclick="switchTab('search-tab')" class="w-full bg-slate-100 hover:bg-slate-200 text-slate-700 font-semibold py-1.5 px-3 rounded-lg text-xs transition">
                                    View Full Inventory
                                </button>
                            </div>
                        </div>
                    ` : `
                        <div class="text-xs text-slate-500 italic">No potential matches currently found in RPF database for this report.</div>
                    `}
                `;
                container.appendChild(matchCard);
            });
        }

        // Track Report / Claim Timeline Status
        function trackStatus() {
            const id = document.getElementById('trackInput').value.trim();
            const resultBox = document.getElementById('trackerResult');

            if (!id) {
                showToast("ID Required", "Please enter a Report or Claim ID to track.", true);
                return;
            }

            const report = lostReports.find(r => r.id.toLowerCase() === id.toLowerCase());

            if (!report) {
                resultBox.classList.remove('hidden');
                resultBox.innerHTML = `
                    <div class="text-center py-6 text-slate-500">
                        <i class="fa-solid fa-circle-xmark text-red-500 text-3xl mb-2"></i>
                        <h3 class="font-bold text-slate-700">No Record Found</h3>
                        <p class="text-xs mt-1">Please check the ID format (e.g., IR-LOST-2026-8841) or submit a new report.</p>
                    </div>
                `;
                return;
            }

            resultBox.classList.remove('hidden');

            let timelineHtml = report.timeline.map((item, idx) => `
                <div class="relative flex items-start space-x-4 mb-6 last:mb-0">
                    ${idx < report.timeline.length - 1 ? `<div class="absolute left-3.5 top-7 bottom-0 w-0.5 ${item.done ? 'bg-emerald-500' : 'bg-slate-200'}"></div>` : ''}
                    <div class="w-7 h-7 rounded-full flex items-center justify-center text-xs font-bold z-10 ${item.done ? 'bg-emerald-500 text-white ring-4 ring-emerald-100' : 'bg-slate-200 text-slate-500'}">
                        ${item.done ? '<i class="fa-solid fa-check"></i>' : (idx + 1)}
                    </div>
                    <div>
                        <div class="text-sm font-bold text-slate-800">${item.step}</div>
                        <div class="text-xs text-slate-400 mt-0.5">${item.time}</div>
                    </div>
                </div>
            `).join('');

            resultBox.innerHTML = `
                <div class="border-b border-slate-200 pb-4 mb-4">
                    <div class="flex justify-between items-start flex-wrap gap-2">
                        <div>
                            <span class="bg-ir-navy text-white font-mono text-xs px-2.5 py-1 rounded font-bold">${report.id}</span>
                            <h3 class="text-lg font-bold text-slate-800 mt-1">${escapeHtml(report.title)}</h3>
                            <p class="text-xs text-slate-500">Passenger: ${escapeHtml(report.name)} | PNR: ${escapeHtml(report.pnr)}</p>
                        </div>
                        <span class="bg-emerald-100 text-emerald-800 border border-emerald-300 text-xs px-3 py-1 rounded-full font-bold">
                            Active Lifecycle
                        </span>
                    </div>
                </div>

                <div class="space-y-2 mb-6 bg-slate-50 p-3 rounded-lg border border-slate-200 text-xs">
                    <div><strong>Train & Location:</strong> ${escapeHtml(report.train)} (${escapeHtml(report.station)})</div>
                    <div><strong>Description:</strong> ${escapeHtml(report.description)}</div>
                </div>

                <h4 class="text-xs font-extrabold uppercase tracking-wider text-slate-400 mb-4">Live Retrieval Progress Timeline</h4>
                <div class="pl-2">
                    ${timelineHtml}
                </div>
            `;
        }

        // Claim Modal Handlers
        function openClaimModal(itemId) {
            const item = foundItems.find(i => i.id === itemId);
            if (!item) return;

            document.getElementById('claimItemId').value = item.id;
            document.getElementById('modalItemTitle').innerText = `${item.title} (${item.id})`;
            document.getElementById('modalItemLocation').innerText = `Location: ${item.station} - ${item.rpfStation}`;

            document.getElementById('claimModal').classList.remove('hidden');
        }

        function closeClaimModal() {
            document.getElementById('claimModal').classList.add('hidden');
            document.getElementById('claimForm').reset();
        }

        function handleClaimSubmit(e) {
            e.preventDefault();

            const itemId = document.getElementById('claimItemId').value;
            const item = foundItems.find(i => i.id === itemId);

            if (item) {
                item.status = "Verification Pending";
                localStorage.setItem('rail_found_items', JSON.stringify(foundItems));
                renderFoundItems(foundItems);
                updateStats();
            }

            closeClaimModal();
            showToast("Claim Ticket Generated!", `Claim verification request sent to RPF station officer. Reference ticket ID: CLM-${Math.floor(100000 + Math.random() * 900000)}`);
        }

        // Helper Utility Functions
        function escapeHtml(str) {
            if (!str) return '';
            return str.replace(/&/g, "&amp;").replace(/</g, "&lt;").replace(/>/g, "&gt;").replace(/"/g, "&quot;").replace(/'/g, "&#039;");
        }

        function showToast(title, message, isError = false) {
            const toast = document.getElementById('toast');
            const toastTitle = document.getElementById('toastTitle');
            const toastMsg = document.getElementById('toastMessage');
            const toastIcon = document.getElementById('toastIcon');

            toastTitle.innerText = title;
            toastMsg.innerText = message;

            if (isError) {
                toastIcon.className = "fa-solid fa-circle-exclamation text-red-400 text-lg";
                toast.classList.replace('border-ir-gold', 'border-red-500');
            } else {
                toastIcon.className = "fa-solid fa-circle-check text-emerald-400 text-lg";
                toast.classList.replace('border-red-500', 'border-ir-gold');
            }

            toast.classList.remove('translate-y-20', 'opacity-0');
            
            setTimeout(() => {
                toast.classList.add('translate-y-20', 'opacity-0');
            }, 4500);
        }
    </script>
</body>
</html>
