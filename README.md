# SSH-CERT-GENERATION

1. Install Build With Parameters Plugin

2. Copy&Paste Jenkinsfile to your repository and create new pipepline with "This project is parameterized" option checked.

3. First deploy will fail and after it fails refresh the page. You should see "Build with Parameters" button.

4. Deploy again with selected parameters and it should generate a PUBLIC & PRIVATE SSH KEY.
