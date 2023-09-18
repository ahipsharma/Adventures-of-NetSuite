# Adventures-of-NetSuite
![NetSuite](https://github.com/ahipsharma/Adventures-of-NetSuite/assets/76726757/f9771583-7f01-48c4-a54a-81336bfa78df)


## Hola peeps!!! Struggling with NetSuite??? Search here might find a solution for your query



### Getting Script paramters

Import - 'N/runtime'module

var myScript = runtime.getCurrentScript();
var scriptParameterValue = myScript.getParameter({
    name: 'INERNAL_ID_OF_THE_PARAMETER_PASSED'
});


Generate PDF:
function genPDF(billPmtId, vendId, pdfTemplate, toAddress, ccAdddress) { //  This function generates the pdf and sends the pdf to the vendor related to the bill payment
        let flag = false; // flag var is set to false which toggles only when the email is sent successfully.
        let rendererPdf = render.create();
        rendererPdf.setTemplateByScriptId({ scriptId: pdfTemplate });
        rendererPdf.addRecord({ templateName: 'record', record: record.load({ type: 'vendorpayment', id: billPmtId }) });
        let renderingPDF = rendererPdf.renderAsPdf();
        renderingPDF.name = "Generated PDF_" + vendId + ".pdf";
        email.send({
            author: 64835, // Yet to figure out
            recipients: [toAddress],
            // cc: [ccAdddress],
            subject: 'Payment Remittance for ' + (billPmtId - vendId),
            body: 'My Email',
            attachments: [renderingPDF],
            relatedRecords: null
        });
        log.debug("Email sent");
        flag = true;
        return flag;
    }
