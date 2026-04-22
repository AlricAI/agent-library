---
name: Task001 Revamp
description: The goal here is to totally revamp my personal website that is contained in this repo.
model: claude-sonnet-4-5
---
The goal here is to totally revamp my personal website that is contained in this repo. 
First and foremost, you should focus on entirely gutting out the colour scheme. The following is the colour scheme specification with ideas on how to combine the colours (though it is written in HTML, so you'll have to parse it out):

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Scholarly Teal Brand Palette</title>
    <style>
        body {
            font-family: 'Georgia', serif;
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            margin: 0;
            padding: 40px 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1000px;
            margin: 0 auto;
        }
        
        h1 {
            text-align: center;
            color: #2c3e50;
            font-size: 2.5rem;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.1);
        }
        
        .subtitle {
            text-align: center;
            color: #5a6c7d;
            font-size: 1.2rem;
            margin-bottom: 50px;
            font-style: italic;
        }
        
        .main-palette {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            margin-bottom: 50px;
        }
        
        .palette-title {
            font-size: 2rem;
            font-weight: bold;
            text-align: center;
            margin-bottom: 30px;
            color: #2c3e50;
        }
        
        .main-color-strip {
            display: flex;
            height: 80px;
            border-radius: 15px;
            overflow: hidden;
            margin-bottom: 30px;
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }
        
        .main-color-segment {
            flex: 1;
            transition: flex 0.3s ease;
            position: relative;
        }
        
        .main-color-segment:hover {
            flex: 1.3;
        }
        
        .color-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(80px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }
        
        .color-swatch {
            aspect-ratio: 1;
            border-radius: 15px;
            display: flex;
            align-items: end;
            justify-content: center;
            padding: 15px;
            cursor: pointer;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            box-shadow: 0 4px 15px rgba(0,0,0,0.1);
        }
        
        .color-swatch:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.2);
        }
        
        .color-code {
            background: rgba(255,255,255,0.95);
            padding: 6px 10px;
            border-radius: 8px;
            font-size: 0.85rem;
            font-family: 'Courier New', monospace;
            font-weight: bold;
            color: #2c3e50;
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255,255,255,0.3);
        }
        
        .section {
            background: white;
            border-radius: 15px;
            padding: 30px;
            margin-bottom: 30px;
            box-shadow: 0 8px 20px rgba(0,0,0,0.08);
        }
        
        .section h2 {
            color: #008080;
            font-size: 1.6rem;
            margin-bottom: 25px;
            text-align: center;
            border-bottom: 3px solid #40e0d0;
            padding-bottom: 10px;
        }
        
        .combinations {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }
        
        .combination {
            border: 2px solid #e9ecef;
            border-radius: 12px;
            padding: 20px;
            background: #fafbfc;
            transition: all 0.3s ease;
        }
        
        .combination:hover {
            border-color: #20b2aa;
            transform: translateY(-2px);
        }
        
        .combination h4 {
            margin: 0 0 15px;
            color: #2c3e50;
            font-size: 1.1rem;
        }
        
        .combo-colors {
            display: flex;
            gap: 8px;
            margin-bottom: 12px;
        }
        
        .combo-color {
            width: 30px;
            height: 30px;
            border-radius: 6px;
            border: 2px solid white;
            box-shadow: 0 2px 8px rgba(0,0,0,0.1);
        }
        
        .combo-use {
            font-size: 0.85rem;
            color: #6c757d;
            line-height: 1.4;
        }
        
        @media (max-width: 768px) {
            .color-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 15px;
            }
            
            .combinations {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Scholarly Teal</h1>
        <p class="subtitle">Complete Brand Palette - 11 Colors</p>
        
        <div class="main-palette">
            <h2 class="palette-title">Full Color Range</h2>
            
            <div class="main-color-strip">
                <div class="main-color-segment" style="background: #191970;"></div>
                <div class="main-color-segment" style="background: #0891b2;"></div>
                <div class="main-color-segment" style="background: #008080;"></div>
                <div class="main-color-segment" style="background: #20b2aa;"></div>
                <div class="main-color-segment" style="background: #40e0d0;"></div>
                <div class="main-color-segment" style="background: #800020;"></div>
                <div class="main-color-segment" style="background: #ff4b44;"></div>
                <div class="main-color-segment" style="background: #4f5d75;"></div>
                <div class="main-color-segment" style="background: #9ca3af;"></div>
                <div class="main-color-segment" style="background: #ecf4f7;"></div>
                <div class="main-color-segment" style="background: #f8f8ff;"></div>
            </div>
            
            <div class="color-grid">
                <div class="color-swatch" style="background: #191970;">
                    <span class="color-code">#191970</span>
                </div>
                <div class="color-swatch" style="background: #0891b2;">
                    <span class="color-code">#0891B2</span>
                </div>
                <div class="color-swatch" style="background: #008080;">
                    <span class="color-code">#008080</span>
                </div>
                <div class="color-swatch" style="background: #20b2aa;">
                    <span class="color-code">#20B2AA</span>
                </div>
                <div class="color-swatch" style="background: #40e0d0;">
                    <span class="color-code">#40E0D0</span>
                </div>
                <div class="color-swatch" style="background: #800020;">
                    <span class="color-code">#800020</span>
                </div>
                <div class="color-swatch" style="background: #ff4b44;">
                    <span class="color-code">#FF4B44</span>
                </div>
                <div class="color-swatch" style="background: #4f5d75;">
                    <span class="color-code">#4F5D75</span>
                </div>
                <div class="color-swatch" style="background: #9ca3af;">
                    <span class="color-code">#9CA3AF</span>
                </div>
                <div class="color-swatch" style="background: #ecf4f7;">
                    <span class="color-code">#ECF4F7</span>
                </div>
                <div class="color-swatch" style="background: #f8f8ff;">
                    <span class="color-code">#F8F8FF</span>
                </div>
            </div>
        </div>
        
        <div class="section">
            <h2>Website Color Combinations</h2>
            <div class="combinations">
                <div class="combination">
                    <h4>Professional Header</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #191970;"></div>
                        <div class="combo-color" style="background: #f8f8ff;"></div>
                        <div class="combo-color" style="background: #008080;"></div>
                    </div>
                    <div class="combo-use">Navy background, ghost white text, teal accents for navigation</div>
                </div>

                <div class="combination">
                    <h4>Hero Section</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #008080;"></div>
                        <div class="combo-color" style="background: #ecf4f7;"></div>
                        <div class="combo-color" style="background: #ff4b44;"></div>
                    </div>
                    <div class="combo-use">Teal primary, light background, electric coral CTA button</div>
                </div>
                
                <div class="combination">
                    <h4>Content Cards</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #f8f8ff;"></div>
                        <div class="combo-color" style="background: #4f5d75;"></div>
                        <div class="combo-color" style="background: #40e0d0;"></div>
                    </div>
                    <div class="combo-use">Ghost white background, slate text, turquoise highlights</div>
                </div>
                
                <div class="combination">
                    <h4>Academic Focus</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #800020;"></div>
                        <div class="combo-color" style="background: #ecf4f7;"></div>
                        <div class="combo-color" style="background: #191970;"></div>
                    </div>
                    <div class="combo-use">Burgundy headers, light blue-grey background, navy text</div>
                </div>
                
                <div class="combination">
                    <h4>Modern Interface</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #20b2aa;"></div>
                        <div class="combo-color" style="background: #9ca3af;"></div>
                        <div class="combo-color" style="background: #ff4b44;"></div>
                    </div>
                    <div class="combo-use">Light sea green primary, accessible grey text, electric coral interactions</div>
                </div>
                
                <div class="combination">
                    <h4>Alert/Success States</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #40e0d0;"></div>
                        <div class="combo-color" style="background: #ff4b44;"></div>
                        <div class="combo-color" style="background: #800020;"></div>
                    </div>
                    <div class="combo-use">Turquoise success, electric coral warning, burgundy error</div>
                </div>
                
                <div class="combination">
                    <h4>Subtle Backgrounds</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #ecf4f7;"></div>
                        <div class="combo-color" style="background: #f8f8ff;"></div>
                        <div class="combo-color" style="background: #9ca3af;"></div>
                    </div>
                    <div class="combo-use">Layered light backgrounds with accessible grey dividers</div>
                </div>
                
                <div class="combination">
                    <h4>High Contrast</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #191970;"></div>
                        <div class="combo-color" style="background: #f8f8ff;"></div>
                        <div class="combo-color" style="background: #40e0d0;"></div>
                    </div>
                    <div class="combo-use">Navy backgrounds, white text, turquoise highlights</div>
                </div>
            </div>
        </div>
        
        <div class="section">
            <h2>Chart & Figure Combinations</h2>
            <div class="combinations">
                <div class="combination">
                    <h4>Data Visualization - Primary</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #008080;"></div>
                        <div class="combo-color" style="background: #20b2aa;"></div>
                        <div class="combo-color" style="background: #0891b2;"></div>
                        <div class="combo-color" style="background: #ff4b44;"></div>
                        <div class="combo-color" style="background: #191970;"></div>
                    </div>
                    <div class="combo-use">Ideal for bar charts, line graphs - teal family with electric coral and navy accents</div>
                </div>
                
                <div class="combination">
                    <h4>Academic Charts</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #800020;"></div>
                        <div class="combo-color" style="background: #191970;"></div>
                        <div class="combo-color" style="background: #008080;"></div>
                        <div class="combo-color" style="background: #4f5d75;"></div>
                        <div class="combo-color" style="background: #9ca3af;"></div>
                    </div>
                    <div class="combo-use">Perfect for research publications, scholarly presentations, formal reports</div>
                </div>
                
                <div class="combination">
                    <h4>Modern Dashboards</h4>
                    <div class="combo-colors">
                        <div class="combo-color" style="background: #40e0d0;"></div>
                        <div class="combo-color" style="background: #0891b2;"></div>
                        <div class="combo-color" style="background: #ff4b44;"></div>
                        <div class="combo-color" style="background: #4f5d75;"></div>
                        <div class="combo-color" style="background: #ecf4f7;"></div>
                    </div>
                    <div class="combo-use">Fresh, contemporary look for interactive dashboards and web applications</div>
                </div>
            </div>
        </div>
       
<script>
        // Add click functionality to copy color codes
        document.querySelectorAll('.color-swatch').forEach(swatch => {
            swatch.addEventListener('click', function() {
                const colorCode = this.querySelector('.color-code').textContent;
                navigator.clipboard.writeText(colorCode).then(() => {
                    // Brief visual feedback
                    const original = this.style.transform;
                    this.style.transform = 'scale(0.95)';
                    setTimeout(() => {
                        this.style.transform = original;
                    }, 150);
                });
            });
        });
    </script>
</body>
</html>

Secondly, I would like to use tailwind CSS instead of bootstrap, so please remove all bootstrap.

Thirdly, think about how to better optimise this website for mobile, it currently looks boring with no image of me.

Fourthly, I want you to add the attached website logo to the top left of the website header and ensure the surrounding colours complement it.

In terms of implementation:
- This is a GitHub pages website, so you can't use multiple pages (there will likely be other constraints too)
- I am predominantly a python user, with some JavaScript knowledge, so please bare this in mind

On completion:
- Check the website visually to see it still functions correctly and adheres to the colour scheme
- Clean up after yourself by deleting/removing any code or files to do with old colour schemes or bootstrap
- Rewrite documentation (e.g. README) detailing updates, and add a version history to the bottom

Think extremely hard on how to implement all the points I raised.
Make a to-do list to ensure you tackle tasks step by step.