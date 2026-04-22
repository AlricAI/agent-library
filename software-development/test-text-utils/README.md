# Test Text Utils

> # Licensed under the Apache License, Version 2.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# ========= Copyright 2023-2026 @ CAMEL-AI.org. All Rights Reserved. =========
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
# ========= Copyright 2023-2026 @ CAMEL-AI.org. All Rights Reserved. =========
import apps.agents.text_utils as text_utils


def test_split_markdown_code_newline():
    inp = (
        "Solution: To preprocess the historical stock data, we "
        "can perform the following steps:\n\n1. Remove any unnecessary"
        " columns that do not contribute to the prediction, such as"
        " the stock symbol or date.\n2. Check for and handle any "
        "missing or null values in the data.\n3. Normalize the data"
        " to ensure that all features are on the same scale. This "
        "can be done using techniques such as Min-Max scaling or "
        "Z-score normalization.\n4. Split the data into training "
        "and testing sets. The training set will be used to train "
        "the machine learning model, while the testing set will be "
        "used to evaluate its performance.\n\nHere is an example "
        "code snippet to preprocess the data using Pandas:\n\n```\n"
        "import pandas as pd\nfrom sklearn.preprocessing import "
        "MinMaxScaler\nfrom sklearn.model_selection import "
        "train_test_split\n\n# Read in the historical stock data\ndata"
        " = pd.read_csv('historical_stock_data.csv')\n\n# Remove "
        "unnecessary columns\ndata = data.drop(['symbol', 'date'], "
        "axis=1)\n\n# Handle missing values\ndat

*[truncated — see source for full prompt]*