# Crediflow Assignment 

## If I had a few extra days, given optimizations or enhancements would I propose to this task

1. I used OCR (Optical Character Recognition) to extract text from the scanned PDF. Technically, I could use a multimodal model for this, but open-source OCR tools are already really good at handling text extraction from scanned documents. That said, if the document's formatting is all over the place, switching to a multimodal approach might work better.

2. Right now, I’m passing the entire financial report into the model, but that’s not the most efficient way to do it. If financial reports from different companies follow a similar structure, I could optimize the process by only sending the relevant sections to the LLM. This would cut down on token usage and make the process faster. Plus, fine-tuning the LLM specifically for financial reports could be a great long-term solution.

3. Token usage could be reduced even further if we know that the Balance Sheet, Income Statement, and Cash Flow sections always appear on certain pages. Instead of processing the whole document, I could just extract those specific pages and send only what’s necessary to the model. That would make everything way more efficient.