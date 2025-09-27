"<!DOCTYPE html>
<html lang=\"en\">
<head>
    <meta charset=\"UTF-8\">
    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">
    <title>Hayun — Upload Image — Free Image Hosting</title>
    <meta name=\"description\" content=\"Free image hosting and sharing service, upload pictures, photo host. Offers integration solutions for uploading images to forums.\">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, \"Segoe UI\", Roboto, Oxygen, Ubuntu, Cantarell, \"Open Sans\", \"Helvetica Neue\", sans-serif;
            background-color: #111827;
            color: #ffffff;
            line-height: 1.6;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header Styles */
        .header {
            background-color: #111827;
            border-bottom: 1px solid #374151;
            position: sticky;
            top: 0;
            z-index: 50;
            padding: 12px 0;
        }

        .header-content {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .header-left {
            display: flex;
            align-items: center;
            gap: 16px;
        }

        .header-center {
            flex: 1;
            text-align: center;
        }

        .logo {
            font-size: 24px;
            font-weight: bold;
            color: #06b6d4;
            text-decoration: none;
            transition: color 0.3s;
        }

        .logo:hover {
            color: #67e8f9;
        }

        .header-right {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .btn {
            padding: 8px 16px;
            border: none;
            border-radius: 6px;
            font-size: 14px;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            gap: 8px;
        }

        .btn-ghost {
            background: transparent;
            color: #d1d5db;
            border: 1px solid transparent;
        }

        .btn-ghost:hover {
            background-color: #1f2937;
            color: #ffffff;
        }

        .btn-primary {
            background-color: #0891b2;
            color: #ffffff;
        }

        .btn-primary:hover {
            background-color: #0e7490;
            transform: scale(1.05);
        }

        /* Hero Section */
        .hero {
            background: linear-gradient(to bottom, #111827, #1f2937);
            min-height: 60vh;
            display: flex;
            align-items: center;
            padding: 64px 0;
        }

        .hero-content {
            text-align: center;
            max-width: 1000px;
            margin: 0 auto;
        }

        .hero h1 {
            font-size: clamp(2.5rem, 5vw, 4rem);
            font-weight: bold;
            margin-bottom: 24px;
            line-height: 1.2;
        }

        .hero p {
            font-size: clamp(1.1rem, 2vw, 1.5rem);
            color: #d1d5db;
            margin-bottom: 32px;
            max-width: 800px;
            margin-left: auto;
            margin-right: auto;
        }

        .accent {
            color: #06b6d4;
            font-weight: 600;
        }

        .btn-hero {
            padding: 12px 32px;
            font-size: 18px;
            margin-bottom: 48px;
        }

        /* Upload Dropzone */
        .upload-section {
            margin-top: 32px;
        }

        .dropzone {
            border: 2px dashed #4b5563;
            border-radius: 12px;
            padding: 48px;
            text-align: center;
            transition: all 0.3s;
            background-color: rgba(31, 41, 55, 0.5);
            margin-bottom: 24px;
        }

        .dropzone:hover {
            border-color: #6b7280;
            background-color: rgba(31, 41, 55, 0.7);
        }

        .dropzone.drag-over {
            border-color: #06b6d4;
            background-color: rgba(6, 182, 212, 0.1);
        }

        .upload-icon {
            width: 48px;
            height: 48px;
            background-color: #374151;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            margin: 0 auto 16px;
        }

        .dropzone h3 {
            font-size: 20px;
            margin-bottom: 8px;
        }

        .dropzone p {
            color: #9ca3af;
            margin-bottom: 16px;
        }

        .upload-controls {
            display: flex;
            flex-wrap: wrap;
            gap: 12px;
            justify-content: center;
            align-items: center;
        }

        .url-input {
            padding: 8px 12px;
            background-color: #374151;
            border: 1px solid #4b5563;
            border-radius: 6px;
            color: #ffffff;
            width: 250px;
        }

        .url-input::placeholder {
            color: #9ca3af;
        }

        .file-input {
            display: none;
        }

        /* Selected Files */
        .selected-files {
            margin: 24px 0;
        }

        .file-item {
            display: flex;
            align-items: center;
            justify-content: between;
            background-color: #1f2937;
            padding: 12px;
            border-radius: 8px;
            border: 1px solid #374151;
            margin-bottom: 8px;
        }

        .file-info {
            display: flex;
            align-items: center;
            gap: 12px;
            flex: 1;
        }

        .file-details h4 {
            font-size: 14px;
            font-weight: 500;
        }

        .file-details p {
            font-size: 12px;
            color: #9ca3af;
        }

        .remove-btn {
            background: transparent;
            border: none;
            color: #9ca3af;
            cursor: pointer;
            padding: 4px;
            border-radius: 4px;
        }

        .remove-btn:hover {
            color: #ef4444;
            background-color: rgba(239, 68, 68, 0.1);
        }

        /* Upload Options */
        .upload-options {
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
            align-items: end;
            margin: 24px 0;
        }

        .form-group {
            flex: 1;
            min-width: 200px;
        }

        .form-group label {
            display: block;
            font-size: 14px;
            font-weight: 500;
            color: #d1d5db;
            margin-bottom: 8px;
        }

        .select {
            width: 100%;
            padding: 8px 12px;
            background-color: #374151;
            border: 1px solid #4b5563;
            border-radius: 6px;
            color: #ffffff;
        }

        /* Progress Bar */
        .progress-container {
            margin: 24px 0;
            display: none;
        }

        .progress-info {
            display: flex;
            justify-content: space-between;
            font-size: 14px;
            margin-bottom: 8px;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background-color: #374151;
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background-color: #06b6d4;
            width: 0%;
            transition: width 0.3s;
        }

        /* Upload Results */
        .upload-results {
            display: none;
            margin-top: 32px;
        }

        .result-card {
            background-color: #1f2937;
            border: 1px solid #374151;
            border-radius: 8px;
            padding: 24px;
            margin-bottom: 16px;
        }

        .result-content {
            display: flex;
            gap: 24px;
            flex-wrap: wrap;
        }

        .result-image {
            width: 128px;
            height: 128px;
            object-fit: cover;
            border-radius: 8px;
            border: 1px solid #4b5563;
        }

        .result-details {
            flex: 1;
            min-width: 300px;
        }

        .result-details h4 {
            font-size: 18px;
            font-weight: 600;
            margin-bottom: 8px;
        }

        .result-details .meta {
            font-size: 14px;
            color: #9ca3af;
            margin-bottom: 16px;
        }

        .embed-codes h5 {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 12px;
        }

        .embed-row {
            display: flex;
            align-items: center;
            gap: 8px;
            margin-bottom: 8px;
        }

        .embed-label {
            color: #d1d5db;
            font-size: 14px;
            width: 80px;
            flex-shrink: 0;
        }

        .embed-input {
            flex: 1;
            padding: 6px 12px;
            background-color: #374151;
            border: 1px solid #4b5563;
            border-radius: 4px;
            color: #d1d5db;
            font-size: 12px;
        }

        .copy-btn {
            padding: 6px 12px;
            font-size: 12px;
        }

        /* Pricing Section */
        .pricing {
            background-color: #111827;
            padding: 64px 0;
        }

        .pricing-header {
            text-align: center;
            margin-bottom: 48px;
        }

        .pricing h2 {
            font-size: 36px;
            font-weight: bold;
            margin-bottom: 16px;
        }

        .pricing-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 24px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .pricing-card {
            background-color: #1f2937;
            border: 1px solid #374151;
            border-radius: 12px;
            padding: 32px 24px;
            position: relative;
            transition: all 0.3s;
        }

        .pricing-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .pricing-card.popular {
            border-color: #06b6d4;
            box-shadow: 0 0 0 1px #06b6d4;
        }

        .discount-badge {
            position: absolute;
            top: -12px;
            right: -12px;
            padding: 4px 12px;
            border-radius: 16px;
            font-size: 12px;
            font-weight: bold;
            color: white;
            transform: rotate(12deg);
        }

        .badge-red { background-color: #dc2626; }
        .badge-orange { background-color: #ea580c; }

        .plan-name {
            text-align: center;
            font-size: 16px;
            font-weight: 600;
            color: #9ca3af;
            margin-bottom: 16px;
        }

        .plan-price {
            text-align: center;
            margin-bottom: 8px;
        }

        .plan-price .currency {
            font-size: 24px;
            font-weight: bold;
        }

        .plan-price .amount {
            font-size: 48px;
            font-weight: bold;
        }

        .plan-billing {
            text-align: center;
            font-size: 14px;
            color: #9ca3af;
            margin-bottom: 24px;
        }

        .plan-features {
            list-style: none;
            margin: 24px 0;
        }

        .plan-features li {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 6px 0;
            font-size: 14px;
            color: #d1d5db;
        }

        .check-icon {
            color: #06b6d4;
            width: 16px;
            height: 16px;
        }

        .upgrade-btn {
            width: 100%;
            padding: 12px;
            font-weight: 600;
            margin-bottom: 16px;
        }

        .btn-red { background-color: #dc2626; }
        .btn-red:hover { background-color: #b91c1c; }
        .btn-cyan { background-color: #0891b2; }
        .btn-cyan:hover { background-color: #0e7490; }
        .btn-gray { background-color: #4b5563; }
        .btn-gray:hover { background-color: #374151; }

        /* Footer */
        .footer {
            background-color: #111827;
            border-top: 1px solid #374151;
            padding: 32px 0;
            text-align: center;
        }

        .footer p {
            color: #9ca3af;
            font-size: 14px;
        }

        /* Supported Formats */
        .supported-formats {
            text-align: center;
            margin-top: 16px;
        }

        .supported-formats p {
            color: #9ca3af;
            font-size: 14px;
        }

        /* Toast Notification */
        .toast {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background-color: #1f2937;
            border: 1px solid #374151;
            border-radius: 8px;
            padding: 16px;
            color: #ffffff;
            z-index: 1000;
            transform: translateX(400px);
            transition: transform 0.3s;
        }

        .toast.show {
            transform: translateX(0);
        }

        .toast.success {
            border-color: #10b981;
        }

        .toast.error {
            border-color: #ef4444;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                gap: 16px;
            }

            .header-left,
            .header-right {
                display: none;
            }

            .upload-controls {
                flex-direction: column;
            }

            .url-input {
                width: 100%;
            }

            .upload-options {
                flex-direction: column;
            }

            .result-content {
                flex-direction: column;
            }

            .embed-row {
                flex-direction: column;
                align-items: stretch;
            }

            .embed-label {
                width: auto;
                margin-bottom: 4px;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header class=\"header\">
        <div class=\"container\">
            <div class=\"header-content\">
                <div class=\"header-left\">
                    <button class=\"btn btn-ghost\">About ▼</button>
                    <button class=\"btn btn-ghost\">🌐 EN ▼</button>
                </div>
                
                <div class=\"header-center\">
                    <a href=\"#\" class=\"logo\">Hayun</a>
                </div>
                
                <div class=\"header-right\">
                    <button class=\"btn btn-ghost\">📤 Upload</button>
                    <button class=\"btn btn-ghost\">🔑 Sign in</button>
                    <button class=\"btn btn-primary\">👤 Create account</button>
                </div>
            </div>
        </div>
    </header>

    <!-- Hero Section -->
    <section class=\"hero\">
        <div class=\"container\">
            <div class=\"hero-content\">
                <h1>Upload and share your images.</h1>
                <p>
                    Drag and drop anywhere you want and start uploading your images now. 
                    <span class=\"accent\">32 MB limit</span>. 
                    Direct image links, BBCode and HTML thumbnails.
                </p>
                <button class=\"btn btn-primary btn-hero\" onclick=\"scrollToUpload()\">START UPLOADING</button>
                
                <div class=\"upload-section\" id=\"upload-section\">
                    <!-- Upload Dropzone -->
                    <div class=\"dropzone\" id=\"dropzone\">
                        <div class=\"upload-icon\">📤</div>
                        <h3>Drag and drop or paste images here to upload</h3>
                        <p>You can also browse from your computer or add image URLs.</p>
                        
                        <div class=\"upload-controls\">
                            <button class=\"btn btn-primary\" onclick=\"document.getElementById('fileInput').click()\">
                                🖼️ Browse Files
                            </button>
                            <input type=\"url\" class=\"url-input\" id=\"urlInput\" placeholder=\"Paste image URL here\">
                            <button class=\"btn btn-ghost\" onclick=\"addImageUrl()\">🔗</button>
                        </div>
                        
                        <input type=\"file\" id=\"fileInput\" class=\"file-input\" multiple accept=\"image/*,.pdf\">
                    </div>

                    <!-- Selected Files -->
                    <div class=\"selected-files\" id=\"selectedFiles\" style=\"display: none;\">
                        <h4>Selected Files (<span id=\"fileCount\">0</span>)</h4>
                        <div id=\"fileList\"></div>
                    </div>

                    <!-- Upload Options -->
                    <div class=\"upload-options\">
                        <div class=\"form-group\">
                            <label>Auto delete image</label>
                            <select class=\"select\" id=\"autoDelete\">
                                <option value=\"never\">Don't auto delete</option>
                                <option value=\"5m\">After 5 minutes</option>
                                <option value=\"15m\">After 15 minutes</option>
                                <option value=\"30m\">After 30 minutes</option>
                                <option value=\"1h\">After 1 hour</option>
                                <option value=\"3h\">After 3 hours</option>
                                <option value=\"6h\">After 6 hours</option>
                                <option value=\"12h\">After 12 hours</option>
                                <option value=\"1d\">After 1 day</option>
                                <option value=\"2d\">After 2 days</option>
                                <option value=\"3d\">After 3 days</option>
                                <option value=\"1w\">After 1 week</option>
                                <option value=\"1m\">After 1 month</option>
                            </select>
                        </div>
                        <button class=\"btn btn-primary\" id=\"uploadBtn\" onclick=\"startUpload()\">Upload</button>
                    </div>

                    <!-- Progress Bar -->
                    <div class=\"progress-container\" id=\"progressContainer\">
                        <div class=\"progress-info\">
                            <span id=\"progressText\">Uploading images...</span>
                            <span id=\"progressPercent\">0% complete</span>
                        </div>
                        <div class=\"progress-bar\">
                            <div class=\"progress-fill\" id=\"progressFill\"></div>
                        </div>
                    </div>

                    <!-- Upload Results -->
                    <div class=\"upload-results\" id=\"uploadResults\">
                        <div style=\"text-align: center; margin-bottom: 24px;\">
                            <h3>Upload complete</h3>
                            <p style=\"color: #9ca3af; margin-top: 8px;\">
                                You can create a new album with the content just uploaded. You must create an account or sign in to save this content into your account.
                            </p>
                        </div>
                        <div id=\"resultsList\"></div>
                        <div style=\"text-align: center; margin-top: 24px;\">
                            <button class=\"btn btn-primary\" onclick=\"resetUpload()\">Upload More Images</button>
                        </div>
                    </div>

                    <!-- Supported Formats -->
                    <div class=\"supported-formats\">
                        <p>JPG PNG BMP GIF TIF WEBP HEIC AVIF PDF • 32 MB limit</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Pricing Section -->
    <section class=\"pricing\">
        <div class=\"container\">
            <div class=\"pricing-header\">
                <h2>Hayun Pro account</h2>
                <p style=\"color: #d1d5db; font-size: 18px; max-width: 600px; margin: 0 auto;\">
                    Hayun is a free image hosting service. Upgrade to unlock all the features.
                </p>
            </div>
            
            <div class=\"pricing-grid\">
                <!-- 3 Year Pro -->
                <div class=\"pricing-card popular\">
                    <div class=\"discount-badge badge-red\">69% OFF</div>
                    <div class=\"plan-name\">3 YEAR PRO</div>
                    <div class=\"plan-price\">
                        <span class=\"currency\">$</span><span class=\"amount\">3.99</span>
                    </div>
                    <div class=\"plan-billing\">Billed $143.64</div>
                    <button class=\"btn upgrade-btn btn-red\">UPGRADE</button>
                    <ul class=\"plan-features\">
                        <li><span class=\"check-icon\">✓</span> No Ads</li>
                        <li><span class=\"check-icon\">✓</span> Direct Linking</li>
                        <li><span class=\"check-icon\">✓</span> Unlimited space</li>
                        <li><span class=\"check-icon\">✓</span> Replace image feature</li>
                        <li><span class=\"check-icon\">✓</span> 64 MB file size per image</li>
                        <li><span class=\"check-icon\">✓</span> API Access</li>
                    </ul>
                </div>

                <!-- Annual Plan -->
                <div class=\"pricing-card\">
                    <div class=\"discount-badge badge-orange\">38% OFF</div>
                    <div class=\"plan-name\">ANNUAL PLAN</div>
                    <div class=\"plan-price\">
                        <span class=\"currency\">$</span><span class=\"amount\">7.99</span>
                    </div>
                    <div class=\"plan-billing\">Billed $95.88</div>
                    <button class=\"btn upgrade-btn btn-cyan\">UPGRADE</button>
                    <ul class=\"plan-features\">
                        <li><span class=\"check-icon\">✓</span> No Ads</li>
                        <li><span class=\"check-icon\">✓</span> Direct Linking</li>
                        <li><span class=\"check-icon\">✓</span> Unlimited space</li>
                        <li><span class=\"check-icon\">✓</span> Replace image feature</li>
                        <li><span class=\"check-icon\">✓</span> 64 MB file size per image</li>
                        <li><span class=\"check-icon\">✓</span> API Access</li>
                    </ul>
                </div>

                <!-- Monthly Plan -->
                <div class=\"pricing-card\">
                    <div class=\"plan-name\">MONTHLY PLAN</div>
                    <div class=\"plan-price\">
                        <span class=\"currency\">$</span><span class=\"amount\">12.99</span>
                    </div>
                    <div class=\"plan-billing\">&nbsp;</div>
                    <button class=\"btn upgrade-btn btn-gray\">UPGRADE</button>
                    <ul class=\"plan-features\">
                        <li><span class=\"check-icon\">✓</span> No Ads</li>
                        <li><span class=\"check-icon\">✓</span> Direct Linking</li>
                        <li><span class=\"check-icon\">✓</span> Unlimited space</li>
                        <li><span class=\"check-icon\">✓</span> Replace image feature</li>
                        <li><span class=\"check-icon\">✓</span> 64 MB file size per image</li>
                        <li><span class=\"check-icon\">✓</span> API Access</li>
                    </ul>
                </div>
            </div>
            
            <div style=\"text-align: center; margin-top: 48px;\">
                <p style=\"color: #9ca3af; font-size: 14px;\">
                    All plans include unlimited bandwidth, 99.9% uptime guarantee, and 24/7 customer support. No setup fees or hidden charges.
                </p>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class=\"footer\">
        <div class=\"container\">
            <p>© 2024 Hayun. All rights reserved. Free image hosting service.</p>
        </div>
    </footer>

    <!-- Toast Notification -->
    <div class=\"toast\" id=\"toast\">
        <div id=\"toastMessage\">Upload complete!</div>
    </div>

    <script>
        // Global variables
        let selectedFiles = [];
        let isUploading = false;

        // Initialize event listeners
        document.addEventListener('DOMContentLoaded', function() {
            const dropzone = document.getElementById('dropzone');
            const fileInput = document.getElementById('fileInput');
            const urlInput = document.getElementById('urlInput');

            // Drag and drop events
            dropzone.addEventListener('dragover', handleDragOver);
            dropzone.addEventListener('dragleave', handleDragLeave);
            dropzone.addEventListener('drop', handleDrop);

            // File input change
            fileInput.addEventListener('change', handleFileSelect);

            // URL input enter key
            urlInput.addEventListener('keypress', function(e) {
                if (e.key === 'Enter') {
                    addImageUrl();
                }
            });
        });

        function handleDragOver(e) {
            e.preventDefault();
            document.getElementById('dropzone').classList.add('drag-over');
        }

        function handleDragLeave(e) {
            e.preventDefault();
            document.getElementById('dropzone').classList.remove('drag-over');
        }

        function handleDrop(e) {
            e.preventDefault();
            document.getElementById('dropzone').classList.remove('drag-over');
            const files = Array.from(e.dataTransfer.files);
            addFiles(files);
        }

        function handleFileSelect(e) {
            const files = Array.from(e.target.files);
            addFiles(files);
        }

        function addFiles(files) {
            selectedFiles = [...selectedFiles, ...files];
            updateFileList();
        }

        function addImageUrl() {
            const urlInput = document.getElementById('urlInput');
            const url = urlInput.value.trim();
            
            if (url) {
                const urlFile = {
                    name: url.split('/').pop() || 'image-from-url',
                    size: 0,
                    type: 'image/jpeg',
                    url: url,
                    isUrl: true
                };
                selectedFiles.push(urlFile);
                urlInput.value = '';
                updateFileList();
            }
        }

        function updateFileList() {
            const selectedFilesDiv = document.getElementById('selectedFiles');
            const fileList = document.getElementById('fileList');
            const fileCount = document.getElementById('fileCount');

            if (selectedFiles.length === 0) {
                selectedFilesDiv.style.display = 'none';
                return;
            }

            selectedFilesDiv.style.display = 'block';
            fileCount.textContent = selectedFiles.length;

            fileList.innerHTML = selectedFiles.map((file, index) => `
                <div class=\"file-item\">
                    <div class=\"file-info\">
                        <div style=\"color: #06b6d4;\">🖼️</div>
                        <div class=\"file-details\">
                            <h4>${file.name}</h4>
                            <p>${file.isUrl ? 'From URL' : formatFileSize(file.size)}</p>
                        </div>
                    </div>
                    <button class=\"remove-btn\" onclick=\"removeFile(${index})\">✕</button>
                </div>
            `).join('');
        }

        function removeFile(index) {
            selectedFiles.splice(index, 1);
            updateFileList();
        }

        function formatFileSize(bytes) {
            if (bytes === 0) return '0 Bytes';
            const k = 1024;
            const sizes = ['Bytes', 'KB', 'MB', 'GB'];
            const i = Math.floor(Math.log(bytes) / Math.log(k));
            return parseFloat((bytes / Math.pow(k, i)).toFixed(1)) + ' ' + sizes[i];
        }

        function scrollToUpload() {
            document.getElementById('upload-section').scrollIntoView({ 
                behavior: 'smooth' 
            });
        }

        function startUpload() {
            if (selectedFiles.length === 0) {
                showToast('Please select or drop files to upload', 'error');
                return;
            }

            if (isUploading) return;

            isUploading = true;
            document.getElementById('uploadBtn').disabled = true;
            document.getElementById('progressContainer').style.display = 'block';

            // Simulate upload progress
            simulateUpload();
        }

        function simulateUpload() {
            let progress = 0;
            const progressFill = document.getElementById('progressFill');
            const progressPercent = document.getElementById('progressPercent');

            const interval = setInterval(() => {
                progress += Math.random() * 15;
                if (progress >= 100) {
                    progress = 100;
                    clearInterval(interval);
                    completeUpload();
                }
                
                progressFill.style.width = progress + '%';
                progressPercent.textContent = Math.round(progress) + '% complete';
            }, 200);
        }

        function completeUpload() {
            // Hide upload form and progress
            document.getElementById('dropzone').style.display = 'none';
            document.getElementById('selectedFiles').style.display = 'none';
            document.querySelector('.upload-options').style.display = 'none';
            document.getElementById('progressContainer').style.display = 'none';
            document.querySelector('.supported-formats').style.display = 'none';

            // Show results
            document.getElementById('uploadResults').style.display = 'block';

            // Generate mock results
            const results = selectedFiles.map((file, index) => {
                const id = Date.now() + index;
                const filename = file.name;
                const imageUrl = file.url || `https://picsum.photos/800/600?random=${id}`;
                const directLink = `https://hayun.example.com/${id}/${filename}`;
                
                return {
                    id: id,
                    filename: filename,
                    url: imageUrl,
                    thumbnail: imageUrl,
                    size: file.isUrl ? 'Unknown' : formatFileSize(file.size),
                    directLink: directLink,
                    bbCode: `[img]${directLink}[/img]`,
                    htmlCode: `<img src=\"${directLink}\" alt=\"${filename}\" />`
                };
            });

            displayResults(results);
            showToast(`Successfully uploaded ${results.length} image(s)!`, 'success');
            
            isUploading = false;
        }

        function displayResults(results) {
            const resultsList = document.getElementById('resultsList');
            
            resultsList.innerHTML = results.map(result => `
                <div class=\"result-card\">
                    <div class=\"result-content\">
                        <img src=\"${result.thumbnail}\" alt=\"${result.filename}\" class=\"result-image\">
                        <div class=\"result-details\">
                            <h4>${result.filename}</h4>
                            <div class=\"meta\">${result.size} • Uploaded ${new Date().toLocaleDateString()}</div>
                            
                            <div class=\"embed-codes\">
                                <h5>Embed codes</h5>
                                
                                <div class=\"embed-row\">
                                    <div class=\"embed-label\">Direct link:</div>
                                    <input type=\"text\" class=\"embed-input\" value=\"${result.directLink}\" readonly>
                                    <button class=\"btn copy-btn\" onclick=\"copyToClipboard('${result.directLink}', 'Direct link')\">📋</button>
                                </div>
                                
                                <div class=\"embed-row\">
                                    <div class=\"embed-label\">HTML:</div>
                                    <input type=\"text\" class=\"embed-input\" value=\"${result.htmlCode.replace(/\"/g, '&quot;')}\" readonly>
                                    <button class=\"btn copy-btn\" onclick=\"copyToClipboard('${result.htmlCode}', 'HTML code')\">📋</button>
                                </div>
                                
                                <div class=\"embed-row\">
                                    <div class=\"embed-label\">BBCode:</div>
                                    <input type=\"text\" class=\"embed-input\" value=\"${result.bbCode}\" readonly>
                                    <button class=\"btn copy-btn\" onclick=\"copyToClipboard('${result.bbCode}', 'BBCode')\">📋</button>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            `).join('');
        }

        function copyToClipboard(text, type) {
            navigator.clipboard.writeText(text).then(() => {
                showToast(`${type} copied to clipboard!`, 'success');
            }).catch(() => {
                // Fallback for older browsers
                const textArea = document.createElement('textarea');
                textArea.value = text;
                document.body.appendChild(textArea);
                textArea.select();
                document.execCommand('copy');
                document.body.removeChild(textArea);
                showToast(`${type} copied to clipboard!`, 'success');
            });
        }

        function resetUpload() {
            // Reset all states
            selectedFiles = [];
            isUploading = false;
            
            // Show upload form
            document.getElementById('dropzone').style.display = 'block';
            document.querySelector('.upload-options').style.display = 'flex';
            document.querySelector('.supported-formats').style.display = 'block';
            
            // Hide results
            document.getElementById('uploadResults').style.display = 'none';
            document.getElementById('selectedFiles').style.display = 'none';
            document.getElementById('progressContainer').style.display = 'none';
            
            // Reset form
            document.getElementById('uploadBtn').disabled = false;
            document.getElementById('fileInput').value = '';
            document.getElementById('urlInput').value = '';
            
            // Reset progress
            document.getElementById('progressFill').style.width = '0%';
            document.getElementById('progressPercent').textContent = '0% complete';
        }

        function showToast(message, type = 'success') {
            const toast = document.getElementById('toast');
            const toastMessage = document.getElementById('toastMessage');
            
            toastMessage.textContent = message;
            toast.className = `toast ${type}`;
            toast.classList.add('show');
            
            setTimeout(() => {
                toast.classList.remove('show');
            }, 3000);
        }
    </script>
</body>
</html>"
