[index.html.html](https://github.com/user-attachments/files/29874687/index.html.html)
<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ระบบวิเคราะห์และจองรถขนส่ง | RISEN</title>
    
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Kanit:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <style>
        body { 
            font-family: 'Kanit', sans-serif; 
            background-color: #f1f5f9; 
            min-height: 100vh;
            scroll-behavior: smooth;
            font-size: 1.1rem;
        }
        
        .glass-card {
            background: #ffffff;
            border: 1px solid #e2e8f0;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.05);
            border-radius: 1.5rem;
        }

        .input-professional {
            border: 2px solid #e2e8f0;
            background: #ffffff;
            border-radius: 0.85rem;
            padding: 0.85rem 1.1rem;
            transition: all 0.2s;
            width: 100%;
            font-size: 1.1rem;
        }

        .input-professional:focus {
            border-color: #2563eb; 
            outline: none;
            box-shadow: 0 0 0 4px rgba(37, 99, 235, 0.1);
        }

        .label-bold {
            font-size: 1rem;
            font-weight: 600;
            color: #475569;
            margin-bottom: 0.5rem;
            display: block;
        }

        .section-header {
            font-size: 1.5rem;
            font-weight: 700;
            color: #0f172a;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .type-btn {
            transition: all 0.2s;
            border: 2px solid #e2e8f0;
            background: #ffffff;
            color: #64748b;
            font-size: 1rem;
            font-weight: 600;
        }
        .type-btn.active {
            background: #2563eb; 
            color: white;
            border-color: #2563eb;
            box-shadow: 0 4px 6px -1px rgba(37, 99, 235, 0.2);
        }

        .vehicle-card {
            transition: all 0.2s;
            border: 2px solid #f1f5f9;
            cursor: pointer;
            padding: 1.5rem;
            border-radius: 1.25rem;
            background: #f8fafc;
            text-align: center;
        }
        .vehicle-card:hover {
            border-color: #cbd5e1;
            transform: translateY(-2px);
        }
        .vehicle-card.active {
            border-color: #2563eb; 
            background: #eff6ff;
            box-shadow: 0 10px 15px -3px rgba(37, 99, 235, 0.1);
        }

        .modal-overlay {
            display: none;
            position: fixed;
            inset: 0;
            background: rgba(15, 23, 42, 0.7);
            backdrop-filter: blur(8px);
            z-index: 100;
            align-items: center;
            justify-content: center;
            padding: 1rem;
        }
        .modal-overlay.active { display: flex; }

        .preview-box {
            background: #fdfdfd;
            border: 2px solid #e2e8f0;
            border-radius: 1.25rem;
            font-family: 'Kanit', sans-serif;
            white-space: pre-wrap;
            line-height: 1.6;
            font-size: 1.15rem;
            color: #1e293b;
            width: 100%;
            min-height: 500px;
            padding: 1.75rem;
            outline: none;
            resize: vertical;
        }

        .risen-badge {
            font-size: 0.85rem;
            padding: 0.25rem 0.75rem;
            border-radius: 9999px;
            font-weight: 700;
            text-transform: uppercase;
            margin-bottom: 0.5rem;
            display: inline-block;
        }

        .switch {
            position: relative;
            display: inline-block;
            width: 50px;
            height: 26px;
        }
        .switch input { opacity: 0; width: 0; height: 0; }
        .slider {
            position: absolute;
            cursor: pointer;
            top: 0; left: 0; right: 0; bottom: 0;
            background-color: #cbd5e1;
            transition: .4s;
            border-radius: 34px;
        }
        .slider:before {
            position: absolute;
            content: "";
            height: 18px; width: 18px;
            left: 4px; bottom: 4px;
            background-color: white;
            transition: .4s;
            border-radius: 50%;
        }
        input:checked + .slider { background-color: #10b981; }
        input:checked + .slider:before { transform: translateX(24px); }
    </style>
</head>
<body class="text-slate-800 pb-12">
    <div id="top" class="max-w-7xl mx-auto p-4 lg:p-8">
        <header class="mb-10 flex flex-col md:flex-row justify-between items-start md:items-center gap-6">
            <div class="flex items-center gap-6">
                <div class="bg-blue-600 p-5 rounded-3xl shadow-xl shadow-blue-200">
                    <svg class="w-12 h-12 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M13 10V3L4 14h7v7l9-11h-7z"></path></svg>
                </div>
                <div>
                    <h1 class="text-4xl font-black text-slate-900 leading-tight">
                        ระบบจัดการขนส่งสินค้า
                    </h1>
                    <div class="flex gap-2 items-center mt-2">
                        <span class="bg-blue-100 text-blue-700 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-tighter">มาตรฐาน RISEN</span>
                        <p class="text-slate-500 font-medium text-sm">กลยุทธ์ลอจิสติกส์และระบบจองรถอัตโนมัติ</p>
                    </div>
                </div>
            </div>
            <div class="flex flex-wrap gap-3">
                <a href="https://www.google.com/search?q=ราคาน้ำมันวันนี้" target="_blank" class="bg-orange-500 text-white px-6 py-3 rounded-2xl font-bold flex items-center gap-2 hover:bg-orange-600 transition-all shadow-lg shadow-orange-200 text-base">
                    ⛽ เช็คราคาน้ำมัน
                </a>
                <button onclick="toggleHistory(true)" class="bg-white border-2 border-slate-200 text-slate-700 px-6 py-3 rounded-2xl font-bold flex items-center gap-2 hover:bg-slate-50 transition-all shadow-sm text-base">
                    📂 ประวัติงาน
                </button>
            </div>
        </header>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8">
            <div class="lg:col-span-5 space-y-8">
                <div class="glass-card p-8">
                    <span class="risen-badge bg-purple-100 text-purple-600 font-bold">บทบาทและพาหนะ</span>
                    <h2 class="section-header">
                        <span class="bg-blue-100 text-blue-600 p-2.5 rounded-xl"><svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 17a2 2 0 11-4 0 2 2 0 014 0zM19 17a2 2 0 11-4 0 2 2 0 014 0z"></path></svg></span>
                        ประเภทรถขนส่ง
                    </h2>
                    <div class="grid grid-cols-2 gap-4" id="vehicle-grid"></div>
                </div>

                <div class="glass-card p-8">
                    <span class="risen-badge bg-blue-100 text-blue-600 font-bold">รายละเอียดและขอบเขตงาน</span>
                    <h2 class="section-header">
                        <span class="bg-orange-100 text-orange-600 p-2.5 rounded-xl"><svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5H7a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2V7a2 2 0 00-2-2h-2M9 5a2 2 0 002 2h2a2 2 0 002-2M9 5a2 2 0 012-2h2a2 2 0 012 2"></path></svg></span>
                        ข้อมูลรายละเอียดงาน
                    </h2>
                    
                    <div class="flex gap-3 p-1.5 bg-slate-100 rounded-2xl mb-8">
                        <button onclick="setJob('ขาเข้า (Import)')" id="job-Import" class="type-btn active flex-1 py-3 rounded-xl text-sm">Import</button>
                        <button onclick="setJob('ขาออก (Export)')" id="job-Export" class="type-btn flex-1 py-3 rounded-xl text-sm">Export</button>
                        <button onclick="setJob('งานทั่วไป (General)')" id="job-General" class="type-btn flex-1 py-3 rounded-xl text-sm">General</button>
                    </div>

                    <div class="space-y-6">
                        <div>
                            <label class="label-bold">ชื่อลูกค้า / ชื่องาน</label>
                            <input type="text" id="ref-name" oninput="updateBookingPreview()" placeholder="ระบุชื่องาน..." class="input-professional font-bold text-xl">
                        </div>

                        <div id="date-grid" class="grid grid-cols-2 gap-4"></div>

                        <div class="grid grid-cols-2 gap-4">
                            <div>
                                <label class="label-bold">จำนวน (Qty)</label>
                                <input type="number" id="qty" value="1" oninput="updateBookingPreview()" class="input-professional text-center font-bold text-xl">
                            </div>
                            <div>
                                <label class="label-bold">น้ำหนักรวม</label>
                                <input type="text" id="weight" value="25 ตัน" oninput="updateBookingPreview()" class="input-professional text-xl">
                            </div>
                        </div>

                        <div>
                            <label class="label-bold">รายละเอียดสินค้า (เช่น ขนาดตู้)</label>
                            <input type="text" id="size" value="40'HQ" oninput="updateBookingPreview()" class="input-professional text-xl">
                        </div>

                        <div>
                            <label class="label-bold text-blue-600">📝 หมายเหตุเพิ่มเติม</label>
                            <textarea id="job-notes" rows="3" oninput="updateBookingPreview()" class="input-professional text-base" placeholder="เช่น ขอคนขับมีใบขับขี่ประเภท 4..."></textarea>
                        </div>

                        <div id="location-fields" class="space-y-4 pt-4 border-t-2 border-slate-100"></div>
                    </div>
                </div>
            </div>

            <div class="lg:col-span-7 space-y-8">
                <div class="glass-card p-8">
                    <div class="flex justify-between items-center mb-8">
                        <div>
                            <span class="risen-badge bg-orange-100 text-orange-600 font-bold">วิเคราะห์ต้นทุน</span>
                            <h2 class="section-header mb-0">
                                <span class="bg-indigo-100 text-indigo-600 p-2.5 rounded-xl"><svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z"></path></svg></span>
                                คำนวณราคาเสนอขาย
                            </h2>
                        </div>
                    </div>
                    
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-8">
                        <div class="bg-slate-50 p-6 rounded-3xl border-2 border-slate-100">
                            <label class="label-bold text-slate-500 uppercase text-xs">ระยะทางรวม (กม.)</label>
                            <input type="number" id="distance" value="0" oninput="calculate(true)" class="bg-transparent text-5xl font-black text-slate-900 w-full outline-none mt-2">
                        </div>
                        <div class="bg-blue-600 p-6 rounded-3xl text-white shadow-xl shadow-blue-100">
                            <div class="flex justify-between items-start">
                                <label class="label-bold text-blue-200 uppercase text-xs">ราคาที่เสนอขาย (บาท)</label>
                                <span id="margin-badge-display" class="bg-blue-500 text-white text-[10px] px-2 py-0.5 rounded-full font-bold">GP: 0%</span>
                            </div>
                            <input type="number" id="revenue" value="0" oninput="manualRevenueEdit()" class="bg-transparent text-5xl font-black text-white w-full outline-none mt-2">
                        </div>
                    </div>

                    <div class="mb-8 p-6 bg-emerald-50 rounded-3xl border-2 border-emerald-100">
                        <div class="flex items-center justify-between mb-4">
                            <div class="flex items-center gap-4">
                                <div class="w-10 h-10 bg-emerald-500 text-white rounded-xl flex items-center justify-center shadow-lg shadow-emerald-200">
                                    <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M13 7h8m0 0v8m0-8l-8 8-4-4-6 6"></path></svg>
                                </div>
                                <span class="label-bold text-emerald-700 text-lg mb-0">ช่องราคาแนะนำ</span>
                            </div>
                            <div class="flex items-center gap-2 flex-wrap justify-end">
                                <span id="mode-label" class="text-xs font-semibold text-slate-700 bg-slate-100 px-2 py-1 rounded-full whitespace-nowrap">กำหนดเอง</span>
                                <label class="switch">
                                    <input type="checkbox" id="auto-margin-switch" onchange="toggleAutoMargin()">
                                    <span class="slider"></span>
                                </label>
                                <span class="font-bold text-emerald-600">อัตโนมัติ</span>
                            </div>
                        </div>
                        
                        <div class="flex flex-col md:flex-row md:items-center gap-6 pl-14">
                            <div class="flex items-center gap-3">
                                <label class="text-emerald-600 font-bold text-sm">เปอร์เซ็นต์แนะนำ:</label>
                                <input type="number" id="profit-margin-percent" value="0" oninput="calculate(false)" class="bg-white border-2 border-emerald-200 rounded-xl px-4 py-2 text-2xl font-black text-emerald-700 w-28 outline-none">
                                <span class="text-emerald-500 font-black text-2xl">%</span>
                            </div>
                            <div class="bg-white/50 p-3 rounded-2xl border border-emerald-100">
                                <p class="text-emerald-800 text-[11px] font-bold leading-tight">
                                    💡 เกณฑ์แนะนำ: <br>
                                    • ≤ 100 กม. บวก 125% <br>
                                    • > 100 กม. บวก 50%
                                </p>
                            </div>
                        </div>
                    </div>

                    <div class="grid grid-cols-2 md:grid-cols-4 gap-4 mb-6">
                        <div>
                            <label class="label-bold text-sm">ราคาน้ำมัน/ลิตร</label>
                            <input type="number" id="fuel-price" value="34.94" oninput="calculate(false)" class="input-professional text-lg font-bold">
                        </div>
                        <div>
                            <label class="label-bold text-sm">กม./ลิตร</label>
                            <input type="number" id="fuel-rate" value="2.5" oninput="calculate(false)" class="input-professional text-lg font-bold">
                        </div>
                        <!-- Updated block for Fuel Cost Layout -->
                        <div>
                            <div class="flex items-center justify-between mb-1 flex-nowrap">
                                <label class="label-bold text-orange-600 text-sm mb-0 whitespace-nowrap">ค่าน้ำมัน</label>
                                <div class="flex items-center gap-2 justify-end text-xs flex-shrink-0">
                                    <span id="fuel-mode-label" class="font-bold bg-orange-50 text-orange-600 px-2 py-1 rounded-full">อัตโนมัติ</span>
                                    <label class="switch" style="transform:scale(.8)">
                                        <input type="checkbox" id="fuel-auto-switch" checked onchange="
                                            window.fuelEdited=!this.checked;
                                            document.getElementById('fuel-cost-display').readOnly=this.checked;
                                            document.getElementById('fuel-mode-label').textContent=this.checked?'อัตโนมัติ':'กำหนดเอง';
                                            calculate(false);">
                                        <span class="slider"></span>
                                    </label>
                                </div>
                            </div>
                            <input type="number" id="fuel-cost-display" readonly class="input-professional text-lg font-bold bg-orange-50" oninput="window.fuelEdited=!document.getElementById('fuel-auto-switch').checked;calculate(false);">
                        </div>
                        <div>
                            <label class="label-bold text-blue-600 text-sm">หักบริหาร (40%)</label>
                            <input type="number" id="admin-percent" value="40" oninput="calculate(false)" class="input-professional text-lg font-bold border-blue-200 bg-blue-50/30">
                        </div>
                    </div>

                    <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                        <div>
                            <label class="label-bold text-sm">ค่าเสื่อม (บาท/กม.)</label>
                            <input type="number" id="maint-rate" value="1.5" oninput="calculate(false)" class="input-professional text-base">
                        </div>
                        <div>
                            <label class="label-bold text-rose-600 text-sm">พรบ.ภาษีประกัน</label>
                            <input type="number" id="tax-ins-rate" value="1.3" oninput="calculate(false)" class="input-professional text-base border-rose-200 bg-rose-50/20">
                        </div>
                        <div>
                            <label class="label-bold text-sm">ค่าเที่ยวพนักงาน</label>
                            <input type="number" id="driver-fee" value="500" oninput="calculate(false)" class="input-professional text-base">
                        </div>
                        <div>
                            <label class="label-bold text-sm">ค่าทางด่วน/อื่นๆ</label>
                            <input type="number" id="toll-fee" value="0" oninput="calculate(false)" class="input-professional text-base">
                        </div>
                    </div>
                </div>

                <div class="bg-slate-900 rounded-[3rem] p-10 text-white relative overflow-hidden shadow-2xl">
                    <div class="absolute right-0 top-0 w-80 h-80 bg-blue-500/10 rounded-full blur-[100px]"></div>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-10 items-center relative z-10">
                        <div>
                            <p class="text-blue-400 font-bold uppercase tracking-widest text-xs mb-3">กำไรสุทธิโดยประมาณ</p>
                            <div class="flex items-baseline gap-3">
                                <span id="profit-val" class="text-7xl font-black">0</span>
                                <span class="text-2xl text-slate-500 font-bold">฿</span>
                            </div>
                            
                            <div class="mt-10 pt-8 border-t border-white/10 flex gap-10">
                                <div>
                                    <p class="text-slate-500 text-xs font-bold uppercase mb-2">ต้นทุนรวม</p>
                                    <p class="text-3xl font-bold" id="total-cost-val">0</p>
                                </div>
                                <div>
                                    <p class="text-slate-500 text-xs font-bold uppercase mb-2">ต้นทุน/กม.</p>
                                    <p class="text-3xl font-bold text-blue-400" id="cpk-val">0.00</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="flex flex-col gap-4">
                            <button id="copy-btn" onclick="copyBookingText()" class="bg-blue-600 hover:bg-blue-500 text-white py-5 rounded-2xl font-black text-xl flex items-center justify-center gap-4 transition-all active:scale-95 shadow-xl shadow-blue-600/20">
                                <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2.5" d="M8 5H6a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1M8 5a2 2 0 00-2 2v12a2 2 0 002 2h10a2 2 0 002-2v-1"></path></svg>
                                คัดลอกข้อความ
                            </button>
                            <button onclick="saveToHistory()" class="bg-slate-800 hover:bg-slate-700 text-white py-4 rounded-xl font-bold text-base flex items-center justify-center gap-3 transition-all">
                                💾 บันทึกเก็บประวัติ
                            </button>
                            <button onclick="toggleSummaryModal(true)" class="bg-white/5 hover:bg-white/10 text-white py-3.5 rounded-xl font-bold text-xs transition-all text-center border border-white/10 uppercase tracking-widest">
                                ดูรายละเอียดต้นทุน →
                            </button>
                        </div>
                    </div>
                </div>

                <div class="glass-card p-8 border-blue-100 bg-blue-50/10">
                    <div class="flex justify-between items-center mb-6">
                        <div>
                            <span class="risen-badge bg-green-100 text-green-600 font-bold">ผลลัพธ์การจอง</span>
                            <h2 class="section-header mb-0">
                                <span class="bg-emerald-500 text-white p-2 rounded-lg"><svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7"></path></svg></span>
                                แพทเทิร์น เช็คราคา/จองรถ
                            </h2>
                        </div>
                    </div>
                    <textarea id="booking-preview" class="preview-box border-slate-200" spellcheck="false"></textarea>
                </div>
            </div>
        </div>
    </div>

    <div id="modal-summary" class="modal-overlay" onclick="if(event.target == this) toggleSummaryModal(false)">
        <div class="bg-white rounded-[2.5rem] w-full max-w-md overflow-hidden shadow-2xl">
            <div class="bg-slate-900 p-8 text-white text-center">
                <h3 class="text-2xl font-black">รายละเอียดต้นทุน</h3>
            </div>
            <div class="p-8 space-y-4" id="summary-list"></div>
            <div class="px-8 pb-8">
                <button onclick="toggleSummaryModal(false)" class="w-full bg-blue-600 text-white py-4 rounded-2xl font-bold">ปิดหน้าต่าง</button>
            </div>
        </div>
    </div>

    <div id="modal-history" class="modal-overlay" onclick="if(event.target == this) toggleHistory(false)">
        <div class="bg-white rounded-[2.5rem] w-full max-w-3xl overflow-hidden shadow-2xl flex flex-col max-h-[85vh]">
            <div class="p-8 border-b-2 border-slate-100 flex justify-between items-center bg-slate-50">
                <h3 class="text-2xl font-black text-slate-900">ประวัติงานย้อนหลัง</h3>
                <button onclick="clearHistory()" class="text-rose-500 font-bold text-sm">ล้างทั้งหมด</button>
            </div>
            <div id="history-content" class="p-8 overflow-y-auto flex-1 space-y-4"></div>
            <div class="p-6 bg-slate-50 text-center border-t-2 border-slate-100">
                <button onclick="toggleHistory(false)" class="bg-slate-900 text-white px-10 py-3 rounded-xl font-bold text-base">ปิดหน้าต่าง</button>
            </div>
        </div>
    </div>

    <script>
        const vehicles = [
            { id: 'v1', name: 'สิบล้อ 3 เพลา', icon: '🚛', fuel: 2.5, maint: 2.5, driver: 1500 },
            { id: 'v2', name: 'หกล้อ 2 เพลา', icon: '🚚', fuel: 4.2, maint: 1.8, driver: 1200 },
            { id: 'v3', name: 'หัวลาก/เทรลเลอร์', icon: '🚜', fuel: 2.5, maint: 3.5, driver: 1800 },
            { id: 'v4', name: 'รถกระบะ/LCL', icon: '📦', fuel: 8.5, maint: 1.2, driver: 1000 }
        ];

        let state = {
            vehicle: vehicles[0],
            job: 'ขาเข้า (Import)',
            isAutoMargin: false,
            totalCost: 0
        };

        window.onload = init;

        function init() {
            renderVehicles();
            setJob('ขาเข้า (Import)');
            calculate(true);
        }

        function renderVehicles() {
            const container = document.getElementById('vehicle-grid');
            container.innerHTML = vehicles.map(v => `
                <div class="vehicle-card ${state.vehicle.id === v.id ? 'active' : ''}" onclick="selectVehicle('${v.id}')">
                    <div class="text-4xl mb-2">${v.icon}</div>
                    <p class="text-sm font-bold text-slate-800 uppercase tracking-tight">${v.name}</p>
                </div>
            `).join('');
        }

        function selectVehicle(id) {
            state.vehicle = vehicles.find(v => v.id === id);
            document.getElementById('fuel-rate').value = state.vehicle.fuel;
            document.getElementById('maint-rate').value = state.vehicle.maint;
            document.getElementById('driver-fee').value = state.vehicle.driver;
            renderVehicles();
            calculate(true);
        }

        function setJob(type) {
            state.job = type;
            document.querySelectorAll('.type-btn').forEach(b => {
                if (type.includes(b.innerText)) b.classList.add('active');
                else b.classList.remove('active');
            });

            const dateGrid = document.getElementById('date-grid');
            const locContainer = document.getElementById('location-fields');

            if (type === 'ขาออก (Export)') {
                dateGrid.innerHTML = `
                    <div class="col-span-2 grid grid-cols-2 gap-4">
                        <div>
                            <label class="label-bold text-sm">🗓️ รับตู้เปล่า</label>
                            <input type="text" id="date-1" oninput="updateBookingPreview()" class="input-professional text-base">
                        </div>
                        <div>
                            <label class="label-bold text-sm">🗓️ วันบรรจุ</label>
                            <input type="text" id="date-2" oninput="updateBookingPreview()" class="input-professional text-base">
                        </div>
                    </div>
                `;
                locContainer.innerHTML = createLocFields(['ลานรับตู้เปล่า (Yard)', 'สถานที่บรรจุ (Factory)', 'สถานที่คืนตู้ (Port)']);
            } else {
                dateGrid.innerHTML = `
                    <div>
                        <label class="label-bold text-sm">🗓️ วันไปรับ</label>
                        <input type="text" id="date-1" oninput="updateBookingPreview()" class="input-professional text-base">
                    </div>
                    <div>
                        <label class="label-bold text-sm">🚚 วันที่ส่ง</label>
                        <input type="text" id="date-2" oninput="updateBookingPreview()" class="input-professional text-base">
                    </div>
                `;
                if (type === 'ขาเข้า (Import)') {
                    locContainer.innerHTML = createLocFields(['ลานรับตู้ (Port/Yard)', 'สถานที่ส่งของ (Factory)', 'ลานคืนตู้ (Return Yard)']);
                } else {
                    locContainer.innerHTML = createLocFields(['จุดรับสินค้า', 'จุดหมายปลายทาง']);
                }
            }
            updateBookingPreview();
        }

        function createLocFields(labels) {
            return labels.map((l, i) => `
                <div>
                    <label class="label-bold text-slate-400 font-medium text-sm">${l}</label>
                    <input type="text" id="loc-${i}" oninput="updateBookingPreview()" class="input-professional bg-slate-50/50 text-base">
                </div>
            `).join('');
        }

        function toggleAutoMargin() {
            const sw=document.getElementById('auto-margin-switch');
            const rev=document.getElementById('revenue');
            const lbl=document.getElementById('mode-label');
            state.isAutoMargin=sw.checked;
            if(state.isAutoMargin){
                rev.readOnly=true;
                rev.classList.add('opacity-70');
                lbl.textContent='AUTO';
                lbl.className='text-xs font-semibold text-white bg-emerald-500 px-2 py-1 rounded-full whitespace-nowrap';
            }else{
                rev.readOnly=false;
                rev.classList.remove('opacity-70');
                lbl.textContent='MANUAL';
                lbl.className='text-xs font-semibold text-slate-700 bg-slate-100 px-2 py-1 rounded-full whitespace-nowrap';
            }

            state.isAutoMargin = document.getElementById('auto-margin-switch').checked;
            calculate(true); 
        }

        function calculate(updateMarginByDistance = false) {
            const dist = parseFloat(document.getElementById('distance').value) || 0;
            const fuelPrice = parseFloat(document.getElementById('fuel-price').value) || 0;
            const fuelRate = parseFloat(document.getElementById('fuel-rate').value) || 0;
            const maintRate = parseFloat(document.getElementById('maint-rate').value) || 0;
            const taxInsRate = parseFloat(document.getElementById('tax-ins-rate').value) || 0;
            const driverFee = parseFloat(document.getElementById('driver-fee').value) || 0;
            const tollFee = parseFloat(document.getElementById('toll-fee').value) || 0;
            const adminPct = parseFloat(document.getElementById('admin-percent').value) || 0;

            if (updateMarginByDistance) {
                if (dist <= 100) {
                    document.getElementById('profit-margin-percent').value = 125;
                } else {
                    document.getElementById('profit-margin-percent').value = 50;
                }
            }

            let autoFuelCost=(dist/fuelRate)*fuelPrice;
            if(updateMarginByDistance){window.fuelEdited=false;}
            if(window.fuelEdited!==true){
                document.getElementById("fuel-cost-display").value=Math.round(autoFuelCost);
            }
            let fuelCost=parseFloat(document.getElementById("fuel-cost-display").value)||0;
            const maintenance = dist * maintRate;
            const taxInsCost = dist * taxInsRate;
            const baseCost = fuelCost + maintenance + taxInsCost + driverFee + tollFee;
            const adminCost = baseCost * (adminPct / 100);
            
            state.totalCost = baseCost + adminCost;

            if (state.isAutoMargin) {
                const margin = parseFloat(document.getElementById('profit-margin-percent').value) || 0;
                document.getElementById('revenue').value = Math.round(state.totalCost * (1 + (margin / 100)));
            }

            updateProfitDisplay();
            updateBookingPreview();
        }

        function manualRevenueEdit() {
            if (state.isAutoMargin) return;
            updateProfitDisplay();
            updateBookingPreview();
        }

        function updateProfitDisplay() {
            const revenue = parseFloat(document.getElementById('revenue').value) || 0;
            const profit = revenue - state.totalCost;
            const gp = revenue > 0 ? (profit / revenue) * 100 : 0;

            document.getElementById('profit-val').innerText = Math.round(profit).toLocaleString();
            document.getElementById('total-cost-val').innerText = Math.round(state.totalCost).toLocaleString();
            document.getElementById('cpk-val').innerText = (state.totalCost / (parseFloat(document.getElementById('distance').value) || 1)).toFixed(2);
            
            const badge = document.getElementById('margin-badge-display');
            badge.innerText = `GP: ${gp.toFixed(1)}%`;
            badge.className = gp > 15 ? "bg-emerald-500 text-white text-[10px] px-2 py-0.5 rounded-full font-bold" : "bg-orange-500 text-white text-[10px] px-2 py-0.5 rounded-full font-bold";
        }

        function updateBookingPreview() {
            const ref = document.getElementById('ref-name').value || '---';
            const qty = document.getElementById('qty').value;
            const size = document.getElementById('size').value;
            const weight = document.getElementById('weight').value;
            const revenue = document.getElementById('revenue').value;
            const notes = document.getElementById('job-notes').value;
            
            const date1 = document.getElementById('date-1')?.value || '';
            const date2 = document.getElementById('date-2')?.value || '';
            
            let locs = [];
            for(let i=0; i<3; i++) {
                const el = document.getElementById(`loc-${i}`);
                if(el) locs.push(el.value);
            }

            let text = `📌 จองรถขนส่ง: ${state.job}\n`;
            text += `🏢 งาน: ${ref}\n`;
            text += `🚛 ประเภทรถ: ${state.vehicle.name}\n`;
            text += `🔢 จำนวน: ${qty} คัน (${size})\n`;
            text += `⚖️ น้ำหนัก: ${weight}\n`;
            text += `--------------------------\n`;
            
            if(state.job === 'ขาออก (Export)') {
                text += `🗓️ รับตู้: ${date1}\n`;
                text += `🗓️ บรรจุ: ${date2}\n`;
            } else {
                text += `🗓️ วันที่: ${date1} ถึง ${date2}\n`;
            }

            text += `📍 เส้นทาง:\n`;
            locs.forEach((l, i) => { if(l) text += `   ${i+1}. ${l}\n`; });
            
            if(notes) text += `\n📝 หมายเหตุ: ${notes}\n`;
            text += `--------------------------\n`;
            text += `💰 ราคาเสนอ: ${Number(revenue).toLocaleString()} บาท`;

            document.getElementById('booking-preview').value = text;
        }

        async function copyBookingText() {
            const text = document.getElementById('booking-preview').value;
            try {
                const textArea = document.createElement("textarea");
                textArea.value = text;
                document.body.appendChild(textArea);
                textArea.select();
                document.execCommand('copy');
                document.body.removeChild(textArea);
                
                const btn = document.getElementById('copy-btn');
                const originalText = btn.innerHTML;
                btn.innerHTML = '✅ คัดลอกสำเร็จ!';
                btn.classList.replace('bg-blue-600', 'bg-emerald-500');
                setTimeout(() => {
                    btn.innerHTML = originalText;
                    btn.classList.replace('bg-emerald-500', 'bg-blue-600');
                }, 2000);
            } catch (err) {}
        }

        function toggleSummaryModal(show) {
            const modal = document.getElementById('modal-summary');
            if (show) {
                modal.classList.add('active');
                const dist = parseFloat(document.getElementById('distance').value) || 0;
                const fuel = parseFloat(document.getElementById("fuel-cost-display").value) || 0;
                const maint = Math.round(dist * (parseFloat(document.getElementById('maint-rate').value) || 0));
                const taxIns = Math.round(dist * (parseFloat(document.getElementById('tax-ins-rate').value) || 0));
                const driver = parseFloat(document.getElementById('driver-fee').value) || 0;
                const toll = parseFloat(document.getElementById('toll-fee').value) || 0;
                
                const baseTotal = fuel + maint + taxIns + driver + toll;
                const admin = Math.round(baseTotal * ((parseFloat(document.getElementById('admin-percent').value) || 0)/100));

                document.getElementById('summary-list').innerHTML = `
                    <div class="flex justify-between"><span>ค่าน้ำมัน:</span><b>${fuel.toLocaleString()}.-</b></div>
                    <div class="flex justify-between"><span>ค่าเสื่อม/ยาง:</span><b>${maint.toLocaleString()}.-</b></div>
                    <div class="flex justify-between text-rose-600"><span>พรบ.ภาษีประกัน:</span><b>${taxIns.toLocaleString()}.-</b></div>
                    <div class="flex justify-between"><span>ค่าเที่ยว:</span><b>${driver.toLocaleString()}.-</b></div>
                    <div class="flex justify-between"><span>ค่าทางด่วน:</span><b>${toll.toLocaleString()}.-</b></div>
                    <div class="flex justify-between text-blue-600"><span>ค่าบริหาร:</span><b>${admin.toLocaleString()}.-</b></div>
                    <hr>
                    <div class="flex justify-between text-lg font-bold"><span>รวมต้นทุน:</span><b>${Math.round(state.totalCost).toLocaleString()}.-</b></div>
                `;
            } else {
                modal.classList.remove('active');
            }
        }

        function saveToHistory() {
            const history = JSON.parse(localStorage.getItem('risen_jobs') || '[]');
            const job = {
                id: Date.now(),
                title: document.getElementById('ref-name').value || 'ไม่มีชื่อโครงการ',
                date: new Date().toLocaleDateString('th-TH'),
                revenue: document.getElementById('revenue').value,
                profit: document.getElementById('profit-val').innerText,
                type: state.job
            };
            history.unshift(job);
            localStorage.setItem('risen_jobs', JSON.stringify(history.slice(0, 50)));
            alert('บันทึกข้อมูลเรียบร้อยแล้ว');
        }

        function toggleHistory(show) {
            const modal = document.getElementById('modal-history');
            if (show) {
                modal.classList.add('active');
                const history = JSON.parse(localStorage.getItem('risen_jobs') || '[]');
                document.getElementById('history-content').innerHTML = history.length ? history.map(h => `
                    <div class="p-6 bg-slate-50 rounded-2xl border border-slate-200 flex justify-between items-center">
                        <div>
                            <p class="text-xs font-bold text-blue-600 uppercase mb-1">${h.type} • ${h.date}</p>
                            <h4 class="text-lg font-bold text-slate-900">${h.title}</h4>
                        </div>
                        <div class="text-right">
                            <p class="text-sm text-slate-500">ราคา: ${Number(h.revenue).toLocaleString()}.-</p>
                            <p class="text-lg font-black text-emerald-600">กำไร: ${h.profit}.-</p>
                        </div>
                    </div>
                `).join('') : '<p class="text-center text-slate-400 py-10">ไม่พบประวัติงาน</p>';
            } else {
                modal.classList.remove('active');
            }
        }

        function clearHistory() {
            if(confirm('ยืนยันการลบประวัติทั้งหมด?')) {
                localStorage.removeItem('risen_jobs');
                toggleHistory(true);
            }
        }
    </script>
</body>
</html>
