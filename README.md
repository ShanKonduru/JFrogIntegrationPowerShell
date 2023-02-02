<h1>Upload .NET/C# Assemblies to Jfrog Artifactory</h1>

<p>This is a PowerShell script that can be used to upload .NET/C# assemblies to Jfrog Artifactory.</p>

<h2>Prerequisites</h2>
<ul>
  <li>Artifactory API Key</li>
  <li>Artifactory URL</li>
  <li>Repository Name</li>
  <li>File Path</li>
</ul>

<h2>Usage</h2>
<ol>
  <li>Replace the placeholder values for `<API-KEY>`, `<ARTIFACTORY-URL>`, `<REPO-NAME>`, and `<FILE-PATH>` in the script with the actual values.</li>
  <li>Run the script in a PowerShell console.</li>
</ol>

<h2>Script</h2>
<pre>
<code>$apiKey = "&lt;API-KEY&gt;"
$jfrogUrl = "https://&lt;ARTIFACTORY-URL&gt;/artifactory/"
$repository = "&lt;REPO-NAME&gt;"
$filePath = "&lt;FILE-PATH&gt;"

$headers = @{
  "X-JFrog-Art-Api" = $apiKey
}

$fileName = Split-Path $filePath -Leaf
$uri = "$jfrogUrl$repository/$fileName"

Invoke-RestMethod -Method Put -Uri $uri -InFile $filePath -Headers $headers

Write-Host "Uploaded $fileName to $repository successfully."
</code>
</pre>

<h2>Output</h2>
<p>The script will display a success message after the file has been uploaded to Artifactory:</p>
<pre>
<code>Uploaded &lt;FILE-NAME&gt; to &lt;REPO-NAME&gt; successfully.
</code>
</pre>
