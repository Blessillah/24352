# 24352
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Report: Smart Agriculture Platform for SDG 2</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Earthly Tech -->
    <!-- Application Structure Plan: The application is structured as a single-page dashboard with a clear top navigation bar allowing users to jump to different sections. This non-linear approach replaces the report's linear format, enabling users to explore the three core AI models at their own pace. The sections are: an 'Overview' to set the context, three interactive 'Model Demonstrations' to make abstract concepts tangible, and a digestible 'Ethical Considerations' section. This structure was chosen to transform passive reading into active exploration, enhancing understanding and engagement by allowing users to 'play' with the model concepts and see simulated results. -->
    <!-- Visualization & Content Choices: 
        - Report Info: SDG Problem -> Goal: Inform -> Viz: Text blocks with icons -> Justification: Sets the stage clearly.
        - Report Info: Yield Prediction Model -> Goal: Compare/Inform -> Viz: Interactive sliders updating a numerical output (JS), Bar Chart for metrics (Chart.js), Scatter Plot for correlation (Chart.js) -> Justification: Makes the regression model tangible and its performance clear.
        - Report Info: Disease Detection Model -> Goal: Inform/Organize -> Viz: Interactive image gallery (HTML/JS), Donut Chart for accuracy (Chart.js), Styled table for confusion matrix (HTML/Tailwind) -> Justification: Provides a direct, visual demonstration of the classification task and its success.
        - Report Info: Anomaly Detection Model -> Goal: Change/Inform -> Viz: Interactive line chart (Chart.js) with button-triggered highlighting (JS) -> Justification: Visualizes the unsupervised model's function on time-series data effectively.
        - Report Info: Ethical Considerations -> Goal: Organize/Inform -> Viz: Interactive accordion (HTML/JS/Tailwind) -> Justification: Breaks down dense text into digestible, user-controlled segments.
    -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body { font-family: 'Inter', sans-serif; }
        .chart-container { position: relative; width: 100%; max-width: 600px; margin-left: auto; margin-right: auto; height: 300px; max-height: 400px; }
        @media (min-width: 768px) { .chart-container { height: 350px; } }
        .nav-link { transition: color 0.3s, border-bottom-color 0.3s; }
        .nav-link.active { border-bottom-color: #2563eb; color: #2563eb; }
        .section { display: none; }
        .section.active { display: block; }
        .accordion-content { max-height: 0; overflow: hidden; transition: max-height 0.5s ease-out; }
    </style>
</head>
<body class="bg-gray-50 text-gray-800">

    <div class="container mx-auto p-4 md:p-8">

        <header class="text-center mb-8">
            <h1 class="text-3xl md:text-5xl font-bold text-gray-900">Smart Agriculture Platform</h1>
            <p class="text-lg md:text-xl text-gray-600 mt-2">An AI-Driven Solution for UN SDG 2: Zero Hunger</p>
        </header>

        <nav class="sticky top-0 bg-gray-50/80 backdrop-blur-sm z-10 mb-8 border-b border-gray-200">
            <ul class="flex justify-center flex-wrap gap-4 md:gap-8 p-4">
                <li><a href="#overview" class="nav-link text-gray-600 hover:text-blue-600 font-medium pb-2 border-b-2 border-transparent">Overview</a></li>
                <li><a href="#yield" class="nav-link text-gray-600 hover:text-blue-600 font-medium pb-2 border-b-2 border-transparent">Yield Prediction</a></li>
                <li><a href="#disease" class="nav-link text-gray-600 hover:text-blue-600 font-medium pb-2 border-b-2 border-transparent">Disease Detection</a></li>
                <li><a href="#anomaly" class="nav-link text-gray-600 hover:text-blue-600 font-medium pb-2 border-b-2 border-transparent">Anomaly Detection</a></li>
                <li><a href="#ethics" class="nav-link text-gray-600 hover:text-blue-600 font-medium pb-2 border-b-2 border-transparent">Ethics</a></li>
            </ul>
        </nav>

        <main>
            <section id="overview" class="section space-y-8">
                <div class="text-center">
                    <h2 class="text-2xl md:text-3xl font-bold text-gray-900">Addressing Food Insecurity with AI</h2>
                    <p class="mt-2 max-w-3xl mx-auto text-gray-600">This project addresses the critical challenge of food insecurity by leveraging artificial intelligence to enhance agricultural efficiency. Our "Smart Agriculture Platform" targets three key problems to help increase food production, reduce waste, and promote sustainability.</p>
                </div>
                <div class="grid md:grid-cols-3 gap-8">
                    <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <div class="flex items-center gap-4">
                            <div class="text-3xl">🌾</div>
                            <h3 class="text-xl font-semibold text-gray-800">Suboptimal Yields</h3>
                        </div>
                        <p class="mt-2 text-gray-600">Farmers often lack predictive insights for precise planting and resource allocation, leading to lower-than-potential harvests. We use AI to forecast yields and guide decision-making.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <div class="flex items-center gap-4">
                            <div class="text-3xl">🌿</div>
                            <h3 class="text-xl font-semibold text-gray-800">Crop Disease</h3>
                        </div>
                        <p class="mt-2 text-gray-600">Late detection of diseases and pests results in substantial crop destruction. Our computer vision model identifies issues from images for early intervention.</p>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <div class="flex items-center gap-4">
                            <div class="text-3xl">💧</div>
                            <h3 class="text-xl font-semibold text-gray-800">Resource Management</h3>
                        </div>
                        <p class="mt-2 text-gray-600">Mismanagement of water and nutrients leads to waste and environmental degradation. Anomaly detection in soil data provides alerts for efficient resource use.</p>
                    </div>
                </div>
            </section>

            <section id="yield" class="section space-y-8">
                <div class="text-center">
                    <h2 class="text-2xl md:text-3xl font-bold text-gray-900">Model 1: Crop Yield Prediction</h2>
                    <p class="mt-2 max-w-3xl mx-auto text-gray-600">This model uses a Neural Network to forecast crop yields based on various environmental and soil factors. By interacting with the controls below, you can see how changes in conditions affect the predicted yield, demonstrating the core of our regression model.</p>
                </div>
                <div class="grid lg:grid-cols-2 gap-8 items-start">
                    <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100 space-y-4">
                        <h3 class="text-xl font-semibold">Interactive Yield Simulator</h3>
                        <div>
                            <label for="temp-slider" class="font-medium">Average Temperature (°C): <span id="temp-value" class="font-bold text-blue-600">25</span></label>
                            <input id="temp-slider" type="range" min="15" max="35" value="25" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        </div>
                        <div>
                            <label for="rainfall-slider" class="font-medium">Annual Rainfall (mm): <span id="rainfall-value" class="font-bold text-blue-600">900</span></label>
                            <input id="rainfall-slider" type="range" min="300" max="1500" value="900" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        </div>
                        <div>
                            <label for="nitrogen-slider" class="font-medium">Nitrogen (kg/ha): <span id="nitrogen-value" class="font-bold text-blue-600">125</span></label>
                            <input id="nitrogen-slider" type="range" min="50" max="200" value="125" class="w-full h-2 bg-gray-200 rounded-lg appearance-none cursor-pointer">
                        </div>
                        <div class="text-center bg-blue-50 p-4 rounded-lg mt-4">
                            <p class="text-lg text-gray-700">Predicted Yield:</p>
                            <p class="text-4xl font-bold text-blue-700"><span id="predicted-yield">6.75</span> tons/ha</p>
                        </div>
                    </div>
                    <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100 space-y-4">
                        <h3 class="text-xl font-semibold text-center">Model Performance</h3>
                        <div class="grid md:grid-cols-2 gap-4">
                            <div class="chart-container h-64 md:h-auto">
                                <canvas id="yieldMetricsChart"></canvas>
                            </div>
                             <div class="chart-container h-64 md:h-auto">
                                <canvas id="yieldCorrelationChart"></canvas>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section id="disease" class="section space-y-8">
                 <div class="text-center">
                    <h2 class="text-2xl md:text-3xl font-bold text-gray-900">Model 2: Crop Disease Detection</h2>
                    <p class="mt-2 max-w-3xl mx-auto text-gray-600">Our Convolutional Neural Network (CNN) analyzes images of crop leaves to detect signs of disease. Select an image below to simulate sending it to our model for classification. This demonstrates the power of computer vision in providing rapid diagnostics for farmers.</p>
                </div>
                <div class="grid lg:grid-cols-2 gap-8 items-start">
                    <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100">
                        <h3 class="text-xl font-semibold mb-4">Interactive Classification</h3>
                        <div class="grid grid-cols-3 gap-4 mb-4">
                            <img src="https://placehold.co/150x150/a7f3d0/166534?text=Healthy+Leaf" alt="Healthy Leaf" class="disease-img cursor-pointer rounded-lg border-4 border-transparent hover:border-blue-500" data-class="Healthy" data-confidence="98.7">
                            <img src="https://placehold.co/150x150/fecaca/991b1b?text=Disease+A" alt="Diseased Leaf A" class="disease-img cursor-pointer rounded-lg border-4 border-transparent hover:border-blue-500" data-class="Disease A" data-confidence="95.2">
                            <img src="https://placehold.co/150x150/fde68a/92400e?text=Disease+B" alt="Diseased Leaf B" class="disease-img cursor-pointer rounded-lg border-4 border-transparent hover:border-blue-500" data-class="Disease B" data-confidence="97.1">
                        </div>
                        <div id="disease-result" class="text-center bg-gray-50 p-4 rounded-lg">
                            <p class="text-lg text-gray-700">Select an image to see the model's prediction.</p>
                        </div>
                    </div>
                     <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100 space-y-4">
                        <h3 class="text-xl font-semibold text-center">Model Performance</h3>
                        <div class="chart-container mx-auto" style="height:250px; max-width:250px;">
                            <canvas id="diseaseAccuracyChart"></canvas>
                        </div>
                        <p class="text-center text-gray-600">The model correctly classifies diseases with high accuracy, enabling timely intervention.</p>
                    </div>
                </div>
            </section>

            <section id="anomaly" class="section space-y-8">
                <div class="text-center">
                    <h2 class="text-2xl md:text-3xl font-bold text-gray-900">Model 3: Soil Data Anomaly Detection</h2>
                    <p class="mt-2 max-w-3xl mx-auto text-gray-600">Using an Isolation Forest algorithm, this unsupervised model monitors real-time soil sensor data to detect unusual patterns that could indicate issues like irrigation failure or chemical imbalances. Click the button to run the detection and see anomalies highlighted on the chart.</p>
                </div>
                 <div class="bg-white p-6 rounded-xl shadow-md border border-gray-100">
                     <div class="flex flex-wrap justify-between items-center mb-4">
                        <h3 class="text-xl font-semibold">Soil Moisture Fluctuation</h3>
                        <button id="detect-anomalies-btn" class="bg-blue-600 text-white font-bold py-2 px-4 rounded-lg hover:bg-blue-700 transition">Detect Anomalies</button>
                    </div>
                    <div class="chart-container" style="height:350px; max-width:none;">
                        <canvas id="anomalyChart"></canvas>
                    </div>
                 </div>
            </section>

            <section id="ethics" class="section">
                 <div class="text-center mb-8">
                    <h2 class="text-2xl md:text-3xl font-bold text-gray-900">Ethical Considerations</h2>
                    <p class="mt-2 max-w-3xl mx-auto text-gray-600">Developing AI for global good requires a commitment to ethical principles. Our project prioritizes fairness, transparency, and sustainability to ensure our solutions are responsible and equitable.</p>
                </div>
                <div class="max-w-4xl mx-auto space-y-4" id="accordion-container">
                </div>
            </section>
        </main>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const navLinks = document.querySelectorAll('.nav-link');
            const sections = document.querySelectorAll('.section');

            const data = {
                yieldMetrics: {
                    mae: 0.68,
                    r2: 0.85 
                },
                diseaseAccuracy: 96,
                anomalyData: {
                    labels: Array.from({ length: 30 }, (_, i) => `Day ${i + 1}`),
                    normal: [28, 30, 32, 31, 29, 28, 27, 26, 29, 31, 33, 34, 12, 11, 35, 36, 34, 32, 30, 29, 28, 30, 31, 33, 45, 46, 32, 30, 28, 27],
                    anomalyIndices: [12, 13, 24, 25]
                },
                yieldCorrelation: Array.from({ length: 50 }, () => ({
                    x: Math.random() * 8 + 2,
                    y: Math.random() * 8 + 2
                })),
                ethicalConsiderations: [
                    { title: "Bias Mitigation", content: "We acknowledge potential biases in datasets (e.g., geographical, crop type). Mitigation strategies include seeking diverse datasets and transparently documenting model limitations." },
                    { title: "Fairness & Accessibility", content: "The solution is designed with accessibility in mind, targeting mobile-first interfaces and considering low-cost deployment to ensure all farmers can benefit." },
                    { title: "Transparency", content: "Model predictions are intended to be interpretable, providing farmers with clear reasons behind recommendations to build trust and facilitate informed decision-making." },
                    { title: "Data Privacy", content: "Strict protocols for data anonymization and security are essential to protect sensitive farmer information, ensuring data ownership and control remain with the farmers." },
                    { title: "Environmental Impact", content: "While AI models consume energy, the platform's overarching goal is to significantly reduce the environmental footprint of agriculture through optimized resource use, leading to a net positive impact." }
                ]
            };
            
            data.yieldCorrelation.forEach(p => {
                p.y = p.x * (0.9 + Math.random() * 0.2) - (Math.random() * 1);
            });

            function navigateTo(hash) {
                sections.forEach(s => s.classList.remove('active'));
                navLinks.forEach(l => l.classList.remove('active'));

                const targetSection = document.querySelector(hash);
                const targetLink = document.querySelector(`a[href="${hash}"]`);

                if (targetSection) targetSection.classList.add('active');
                if (targetLink) targetLink.classList.add('active');
            }

            navLinks.forEach(link => {
                link.addEventListener('click', (e) => {
                    e.preventDefault();
                    const hash = e.target.getAttribute('href');
                    history.pushState(null, null, hash);
                    navigateTo(hash);
                });
            });

            window.addEventListener('popstate', () => {
                navigateTo(location.hash || '#overview');
            });
            
            navigateTo(location.hash || '#overview');

            function createYieldMetricsChart() {
                const ctx = document.getElementById('yieldMetricsChart').getContext('2d');
                new Chart(ctx, {
                    type: 'bar',
                    data: {
                        labels: ['Mean Absolute Error', 'R-squared (R²)'],
                        datasets: [{
                            label: 'Model Performance',
                            data: [data.yieldMetrics.mae, data.yieldMetrics.r2],
                            backgroundColor: ['rgba(239, 68, 68, 0.6)', 'rgba(37, 99, 235, 0.6)'],
                            borderColor: ['rgba(239, 68, 68, 1)', 'rgba(37, 99, 235, 1)'],
                            borderWidth: 1
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        indexAxis: 'y',
                        scales: { x: { beginAtZero: true, max: 1 } },
                        plugins: { legend: { display: false }, title: { display: true, text: 'Performance Metrics' } }
                    }
                });
            }
            
            function createYieldCorrelationChart() {
                const ctx = document.getElementById('yieldCorrelationChart').getContext('2d');
                new Chart(ctx, {
                    type: 'scatter',
                    data: {
                        datasets: [{
                            label: 'Yield Data',
                            data: data.yieldCorrelation,
                            backgroundColor: 'rgba(37, 99, 235, 0.6)',
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        scales: { x: { title: { display: true, text: 'Actual Yield' } }, y: { title: { display: true, text: 'Predicted Yield' } } },
                        plugins: { legend: { display: false }, title: { display: true, text: 'Actual vs. Predicted' } }
                    }
                });
            }

            function createDiseaseAccuracyChart() {
                const ctx = document.getElementById('diseaseAccuracyChart').getContext('2d');
                new Chart(ctx, {
                    type: 'doughnut',
                    data: {
                        labels: ['High Accuracy', 'Margin of Error'],
                        datasets: [{
                            data: [data.diseaseAccuracy, 100 - data.diseaseAccuracy],
                            backgroundColor: ['rgba(22, 163, 74, 0.7)', 'rgba(229, 231, 235, 0.7)'],
                            borderColor: ['rgba(22, 163, 74, 1)', 'rgba(209, 213, 219, 1)'],
                            borderWidth: 1,
                            circumference: 180,
                            rotation: 270,
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        plugins: {
                            legend: { display: false },
                            title: { display: true, text: `Test Accuracy: ${data.diseaseAccuracy}%`, position: 'bottom', font: { size: 16 } }
                        },
                        cutout: '70%'
                    }
                });
            }

            let anomalyChart;
            function createAnomalyChart(highlight = false) {
                const ctx = document.getElementById('anomalyChart').getContext('2d');
                if (anomalyChart) anomalyChart.destroy();
                
                const pointBackgroundColors = data.anomalyData.labels.map((_, i) => 
                    (highlight && data.anomalyData.anomalyIndices.includes(i)) ? 'rgba(239, 68, 68, 1)' : 'rgba(37, 99, 235, 0.6)'
                );

                anomalyChart = new Chart(ctx, {
                    type: 'line',
                    data: {
                        labels: data.anomalyData.labels,
                        datasets: [{
                            label: 'Soil Moisture',
                            data: data.anomalyData.normal,
                            borderColor: 'rgba(37, 99, 235, 0.5)',
                            backgroundColor: 'rgba(37, 99, 235, 0.1)',
                            fill: true,
                            tension: 0.3,
                            pointBackgroundColor: pointBackgroundColors,
                            pointRadius: highlight ? 5 : 3,
                            pointHoverRadius: 7
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        scales: { y: { title: { display: true, text: 'Moisture Level (%)' } } },
                        plugins: { legend: { display: false } }
                    }
                });
            }

            createYieldMetricsChart();
            createYieldCorrelationChart();
            createDiseaseAccuracyChart();
            createAnomalyChart();
            
            document.getElementById('detect-anomalies-btn').addEventListener('click', () => createAnomalyChart(true));
            
            const sliders = ['temp', 'rainfall', 'nitrogen'];
            sliders.forEach(id => {
                const slider = document.getElementById(`${id}-slider`);
                const valueSpan = document.getElementById(`${id}-value`);
                slider.addEventListener('input', () => {
                    valueSpan.textContent = slider.value;
                    updatePredictedYield();
                });
            });

            function updatePredictedYield() {
                const temp = parseFloat(document.getElementById('temp-slider').value);
                const rainfall = parseFloat(document.getElementById('rainfall-slider').value);
                const nitrogen = parseFloat(document.getElementById('nitrogen-slider').value);
                
                const baseYield = 4.0;
                const tempEffect = (temp - 25) * 0.1;
                const rainfallEffect = (rainfall - 900) * 0.002;
                const nitrogenEffect = (nitrogen - 125) * 0.015;
                
                let predictedYield = baseYield + tempEffect + rainfallEffect + nitrogenEffect;
                predictedYield = Math.max(2.0, Math.min(10.0, predictedYield));
                
                document.getElementById('predicted-yield').textContent = predictedYield.toFixed(2);
            }
            
            const diseaseImages = document.querySelectorAll('.disease-img');
            const diseaseResultDiv = document.getElementById('disease-result');
            diseaseImages.forEach(img => {
                img.addEventListener('click', () => {
                    diseaseImages.forEach(i => i.classList.remove('border-blue-500'));
                    img.classList.add('border-blue-500');
                    const className = img.dataset.class;
                    const confidence = img.dataset.confidence;
                    diseaseResultDiv.innerHTML = `
                        <p class="text-lg text-gray-700">Model Prediction:</p>
                        <p class="text-2xl font-bold text-gray-900">${className}</p>
                        <p class="text-md text-gray-600">Confidence: ${confidence}%</p>
                    `;
                });
            });

            const accordionContainer = document.getElementById('accordion-container');
            data.ethicalConsiderations.forEach((item, index) => {
                const accordionItem = document.createElement('div');
                accordionItem.className = 'bg-white rounded-xl shadow-md border border-gray-100 overflow-hidden';
                accordionItem.innerHTML = `
                    <button class="accordion-button w-full text-left p-4 flex justify-between items-center font-semibold text-lg hover:bg-gray-100 transition">
                        <span>${item.title}</span>
                        <span class="accordion-icon transform rotate-0 transition-transform text-blue-600 text-2xl">+</span>
                    </button>
                    <div class="accordion-content px-4">
                        <p class="py-4 text-gray-600 border-t border-gray-200">${item.content}</p>
                    </div>
                `;
                accordionContainer.appendChild(accordionItem);
            });
            
            accordionContainer.addEventListener('click', (e) => {
                const button = e.target.closest('.accordion-button');
                if (button) {
                    const content = button.nextElementSibling;
                    const icon = button.querySelector('.accordion-icon');
                    const isExpanded = content.style.maxHeight !== '0px';

                    if (isExpanded) {
                        content.style.maxHeight = '0px';
                        icon.textContent = '+';
                        icon.classList.remove('rotate-45');
                    } else {
                        content.style.maxHeight = content.scrollHeight + 'px';
                        icon.textContent = '+';
                        icon.classList.add('rotate-45');
                    }
                }
            });
        });
    </script>

</body>
</html>
