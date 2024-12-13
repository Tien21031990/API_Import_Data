https://www.npmjs.com/package/newman
run powershell as admin
 npm install -g newman
 Get-ExecutionPolicy     (hiện unrestricted)  
 xong set policy thành unrestricted bằng lệnh này=> Set-ExecutionPolicy -ExecutionPolicy Unrestricted
 
 ////// 1. run Accounts migration check
newman run Alandia_Migration_Collection_Latest.postman_collection.json -e Staging.postman_environment.json -d customers_se_10.csv --folder AccountSummaryReport -r html
newman run Alandia_Migration_Collection.postman_collection.json -e Live.postman_environment.json -d customers_fi_4.csv --folder AccountSummaryReport -r html
newman run Alandia_Migration_Collection.postman_collection.json -e Live.postman_environment.json -d customers_se_7.csv --folder AccountSummaryReport -r html

newman run Alandia_Migration_Collection.postman_collection.json -e Staging.postman_environment.json -d customers_se_1_1.csv --folder AccountSummaryReport -r html

////// 2. run Accounts' Cases migration check
newman run Alandia_Migration_Collection.postman_collection.json -e Live.postman_environment.json -d casetasks_fi.csv --folder CaseSummarryReport -r html

newman run Alandia_Migration_Collection.postman_collection.json -e Staging.postman_environment.json -d casetasks_se.csv --folder CaseSummarryReport -r html

////// 3.run Accounts Case's Notes migration check
newman run Alandia_Migration_Collection.postman_collection.json -e Live.postman_environment.json -d casetask_tasknotes_fi.csv --folder CaseNoteSummarryReport -r html

newman run Alandia_Migration_Collection.postman_collection.json -e Staging.postman_environment.json -d casetask_tasknotes_se.csv --folder CaseNoteSummarryReport -r html


// run Account Policy Notes migration check ----------Done until notes_se_3.csv-----------
newman run Alandia_Migration_Collection.postman_collection.json -e Live.postman_environment.json -d notes_fi_3_2.csv --folder NoteSummaryReport -r html

newman run Alandia_Migration_Collection.postman_collection.json -e Staging.postman_environment.json -d notes_se.csv --folder NoteSummaryReport -r html

// run Organizations migration check
newman run Alandia_Migration_Collection.postman_collection.json -e Staging.postman_environment.json -d organizations.csv --folder OrganizationSummaryReport -r html
