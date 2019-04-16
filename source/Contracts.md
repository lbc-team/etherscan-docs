# 智能合约(Contracts)

智能合约相关的 API，接口的参数说明请参考[Etherscan API 约定](Introduction.md), 文档中不单独说明。

Newly verified Contracts are synced to the API servers within 5 minutes or less

## 获取已经验证代码合约的**ABI**

[Verified Contract Source Codes](https://etherscan.io/contractsVerified)

```
https://api.etherscan.io/api?module=contract&action=getabi&address=0xBB9bc244D798123fDe783fCc1C72d3Bb8C189413&apikey=YourApiKeyToken
```

A simple sample for retrieving the contractABI using Web3.js and Jquery to interact with a contract

```js
    var Web3 = require('web3');
    var web3 = new Web3(new Web3.providers.HttpProvider());
    var version = web3.version.api;
            
    $.getJSON('http://api.etherscan.io/api?module=contract&action=getabi&address=0xfb6916095ca1df60bb79ce92ce3ea74c37c5d359', function (data) {
        var contractABI = "";
        contractABI = JSON.parse(data.result);
        if (contractABI != ''){
            var MyContract = web3.eth.contract(contractABI);
            var myContractInstance = MyContract.at("0xfb6916095ca1df60bb79ce92ce3ea74c37c5d359");
            var result = myContractInstance.memberId("0xfe8ad7dd2f564a877cc23feea6c0a9cc2e783715");
            console.log("result1 : " + result);            
            var result = myContractInstance.members(1);
            console.log("result2 : " + result);
        } else {
            console.log("Error" );
        }            
    });
```

## 获取已经验证代码合约的**源码**

```
https://api.etherscan.io/api?module=contract&action=getsourcecode&address=0xBB9bc244D798123fDe783fCc1C72d3Bb8C189413&apikey=YourApiKeyToken
```

## [BETA] 验证源代码

```
1. Requires a valid Etherscan APIkey, will reject if otherwise
2. Current daily limit of 100 submissions per day per user (subject to change)
3. Only supports HTTP post due to max transfer size limitations for http get
4. Supports up to 10 different library pairs
5. Contracts that use "imports" will need to have the code concatenated into one file as we do not support "imports" in separate files. You can try using the Blockcat solidity-flattener or SolidityFlattery
6. List of supported solc versions, only solc version v0.4.11 and above is supported. Ex. v0.4.25+commit.59dbf8f1
7. Upon successful submission you will receive a GUID (50 characters) as a receipt.
8. You may use this GUID to track the status of your submission
9. Verified Source Codes will be displayed at contractsVerified
```

See Demo Source Verification Submission Code at[ Source Code Verification Sample ](https://etherscan.io/sourcecode-demo.html)

Source Code Submission Gist (returns a guid as part of the result upon success):

```
    //Submit Source Code for Verification
    $.ajax({
        type: "POST",                       //Only POST supported  
        url: "//api.etherscan.io/api", //Set to the  correct API url for Other Networks
        data: {
            apikey: $('#apikey').val(),                     //A valid API-Key is required        
            module: 'contract',                             //Do not change
            action: 'verifysourcecode',                     //Do not change
            contractaddress: $('#contractaddress').val(),   //Contract Address starts with 0x...     
            sourceCode: $('#sourceCode').val(),             //Contract Source Code (Flattened if necessary)
            contractname: $('#contractname').val(),         //ContractName
            compilerversion: $('#compilerversion').val(),   // see http://etherscan.io/solcversions for list of support versions
            optimizationUsed: $('#optimizationUsed').val(), //0 = Optimization used, 1 = No Optimization
            runs: 200,                                      //set to 200 as default unless otherwise         
            constructorArguements: $('#constructorArguements').val(),   //if applicable
            libraryname1: $('#libraryname1').val(),         //if applicable, a matching pair with libraryaddress1 required
            libraryaddress1: $('#libraryaddress1').val(),   //if applicable, a matching pair with libraryname1 required
            libraryname2: $('#libraryname2').val(),         //if applicable, matching pair required
            libraryaddress2: $('#libraryaddress2').val(),   //if applicable, matching pair required
            libraryname3: $('#libraryname3').val(),         //if applicable, matching pair required
            libraryaddress3: $('#libraryaddress3').val(),   //if applicable, matching pair required
            libraryname4: $('#libraryname4').val(),         //if applicable, matching pair required
            libraryaddress4: $('#libraryaddress4').val(),   //if applicable, matching pair required
            libraryname5: $('#libraryname5').val(),         //if applicable, matching pair required
            libraryaddress5: $('#libraryaddress5').val(),   //if applicable, matching pair required
            libraryname6: $('#libraryname6').val(),         //if applicable, matching pair required
            libraryaddress6: $('#libraryaddress6').val(),   //if applicable, matching pair required
            libraryname7: $('#libraryname7').val(),         //if applicable, matching pair required
            libraryaddress7: $('#libraryaddress7').val(),   //if applicable, matching pair required
            libraryname8: $('#libraryname8').val(),         //if applicable, matching pair required
            libraryaddress8: $('#libraryaddress8').val(),   //if applicable, matching pair required
            libraryname9: $('#libraryname9').val(),         //if applicable, matching pair required
            libraryaddress9: $('#libraryaddress9').val(),   //if applicable, matching pair required
            libraryname10: $('#libraryname10').val(),       //if applicable, matching pair required
            libraryaddress10: $('#libraryaddress10').val()  //if applicable, matching pair required
        },
        success: function (result) {
            console.log(result);
            if (result.status == "1") {
                //1 = submission success, use the guid returned (result.result) to check the status of your submission.
                // Average time of processing is 30-60 seconds
                document.getElementById("postresult").innerHTML = result.status + ";" + result.message + ";" + result.result;
                // result.result is the GUID receipt for the submission, you can use this guid for checking the verification status
            } else {
                //0 = error
                document.getElementById("postresult").innerHTML = result.status + ";" + result.message + ";" + result.result;
            }
            console.log("status : " + result.status);
            console.log("result : " + result.result);
        },
        error: function (result) {
            console.log("error!");
            document.getElementById("postresult").innerHTML = "Unexpected Error"
        }
    });
       
```

Check Source code verification submission status:

```
    //Check Source Code Verification Status
    $.ajax({
        type: "GET",
        url: "//api.etherscan.io/api",
        data: {
            guid: 'ezq878u486pzijkvvmerl6a9mzwhv6sefgvqi5tkwceejc7tvn', //Replace with your Source Code GUID receipt above
            module: "contract",
            action: "checkverifystatus"
        },
        success: function (result) {
            console.log("status : " + result.status);   //0=Error, 1=Pass 
            console.log("message : " + result.message); //OK, NOTOK
            console.log("result : " + result.result);   //result explanation
            $('#guidstatus').html(">> " + result.result);
        },
        error: function (result) {
            alert('error');
        }
    });
            
```

