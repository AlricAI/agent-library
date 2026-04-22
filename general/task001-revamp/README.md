# Task001 Revamp

> The goal here is to totally revamp my personal website that is contained in this repo.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
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
        
   

*[truncated — see source for full prompt]*