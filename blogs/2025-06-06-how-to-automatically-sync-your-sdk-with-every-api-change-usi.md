---
title: "How to Automatically Sync Your SDK with Every API Change Using CI/CD"
url: "https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd"
date: "Fri, 06 Jun 2025 00:00:00 GMT"
author: ""
feed_url: "https://liblab.com/blog/rss.xml"
---
<p>Keeping SDKs in sync with your API can quickly become a bottleneck - especially when manual updates delay your release cycles. Every API change that requires a corresponding SDK update adds friction and risk. By integrating SDK generation into your CI/CD pipeline, you can automate updates, ensure consistency, and streamline the release process.</p>
<p>This post shows how to set up a CI/CD workflow for SDK projects using <a href="https://liblab.com/" rel="noopener noreferrer" target="_blank">liblab</a>. You'll see practical examples with GitHub Actions and learn how to automatically generate and publish SDKs from OpenAPI specs.</p>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="why-cicd-matters-for-sdk-projects">Why CI/CD Matters for SDK Projects<a class="hash-link" href="https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd#why-cicd-matters-for-sdk-projects" title="Direct link to Why CI/CD Matters for SDK Projects">​</a></h2>
<p>Maintaining SDKs manually is time-consuming and error-prone. Every time an API changes, you need to update the SDK, validate it, and publish a new version. Doing this manually across multiple languages is costly and hard to scale.</p>
<p>CI/CD pipelines automate this process. When integrated with tools like liblab, they can:</p>
<ul>
<li>Automatically regenerate SDKs from updated API via OpenAPI specs</li>
<li>Publish <a href="https://liblab.com/docs/tutorials/ci-cd/integrate-with-github-actions" rel="noopener noreferrer" target="_blank">new versions to package managers</a></li>
</ul>
<p>This ensures your SDKs are always current and consistent, enabling faster and more reliable developer experiences.</p>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="project-structure-and-workflow-overview">Project Structure and Workflow Overview<a class="hash-link" href="https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd#project-structure-and-workflow-overview" title="Direct link to Project Structure and Workflow Overview">​</a></h2>
<p>Before diving into the CI/CD configuration, let's take a look at how the components are organized and how they interact.</p>
<p>This setup involves two directories:</p>
<ul>
<li>
<p><a href="https://github.com/mlanlazc/ci-cd-integration" rel="noopener noreferrer" target="_blank">ci-cd-integration</a> - A monorepo that contains the API, the SDK generation config, and a GitHub workflow that triggers SDK generation based on API changes.</p>
<ul>
<li><code>/api</code> contains the API code and serves the OpenAPI spec on the <code>/openapi-json</code> route. In this example, the API is deployed publicly at <a href="https://ci-cd-integration.onrender.com/" rel="noopener noreferrer" target="_blank">https://ci-cd-integration.onrender.com/</a> for easier access to the spec from the GitHub Action. Note that we're using Render's free tier, which can cause the loading to take a bit longer due to the cold start.</li>
<li><code>/sdk-control</code> contains:<!-- -->
<ul>
<li><code>liblab.config.json</code> - The configuration file that defines SDK generation.</li>
<li><code>api.json</code> - The OpenAPI spec used in the last SDK build (used for diffing, this file will be automatically updated before we go on to build the SDK in CI/CD).</li>
</ul>
</li>
</ul>
<p>These two folders can be in separate repositories - it's a matter of personal or team preference. In this example, for simplicity, we're including them in the same repo.</p>
<p>We also have example SDKs of the results of this process if you're interested in seeing what they look like once the CI/CD pipeline is built and the SDKs are generated:</p>
</li>
<li>
<p><a href="https://github.com/mlanlazc/hello-world-sdk-python" rel="noopener noreferrer" target="_blank">hello-world-sdk-python</a> - Contains the generated Python SDK.</p>
</li>
<li>
<p><a href="https://github.com/mlanlazc/hello-world-sdk-typescript" rel="noopener noreferrer" target="_blank">hello-world-sdk-typescript</a> - Contains the generated Typescript SDK.</p>
</li>
</ul>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="workflow-overview">Workflow Overview<a class="hash-link" href="https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd#workflow-overview" title="Direct link to Workflow Overview">​</a></h2>
<p>The goal of this workflow is to <strong>automatically regenerate SDKs and publish a PR to the SDK repository</strong> whenever there's a change in the API.</p>
<p>Here's a brief overview of how it works before we dive into the details:</p>
<ol>
<li>
<p><strong>Deploy the API</strong></p>
<p>When a commit is pushed to <code>main</code>, the <code>deploy-and-sync-sdk.yml</code> GitHub Action deploys the API (in this example, to Render) and then proceeds to sync the SDK.</p>
</li>
<li>
<p><strong>Detect API changes</strong></p>
<p>Once deployed, the action fetches the latest OpenAPI spec from the live API and compares it with the version stored in <code>sdk-control/api.json</code> (used for the previous SDK build). If there are no differences, the action exits.</p>
</li>
<li>
<p><strong>Commit and push the new spec file</strong></p>
<p>If changes are detected, the action commits and pushes the updated <code>api.json</code>.</p>
</li>
<li>
<p><strong>Update the SDK version</strong></p>
<p>In this setup, the minor version is incremented in <code>liblab.config.json</code>.</p>
</li>
<li>
<p><strong>Build the SDK</strong></p>
<p>The build is triggered using the <a href="https://liblab.com/docs/cli/cli-overview-build#liblab-build" rel="noopener noreferrer" target="_blank"><code>liblab build</code></a> command, which takes the updated OpenAPI spec and config file and generates the new SDKs for Python and Typescript.</p>
</li>
<li>
<p><strong>Commit and push the updated config file</strong></p>
</li>
<li>
<p><strong>Create a PR on SDK repositories</strong></p>
<p>Pull requests are created using the <a href="https://liblab.com/docs/cli/cli-overview-publish#liblab-pr" rel="noopener noreferrer" target="_blank"><code>liblab pr</code></a> command.</p>
</li>
</ol>
<p>This setup ensures your SDK always reflects the current state of your API - without manual steps.</p>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="repository-secrets">Repository Secrets<a class="hash-link" href="https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd#repository-secrets" title="Direct link to Repository Secrets">​</a></h2>
<p>To enable CI/CD automation, we'll need to add several secrets to your GitHub repository:</p>
<ul>
<li><code>LIBLAB_GITHUB_TOKEN</code>: A <strong>fine-grained GitHub token</strong> used by liblab to create pull requests to SDK repositories.</li>
<li><code>LIBLAB_TOKEN</code>: A <strong>token</strong> used to authenticate your CI/CD pipeline with the liblab service.</li>
<li><code>RENDER_API_KEY</code>, <code>RENDER_DEPLOY_HOOK_URL</code>, <code>RENDER_SERVICE_ID</code>: Used to trigger redeploys on Render after API changes.</li>
</ul>
<div class="theme-admonition theme-admonition-note admonition_xJq3 alert alert--secondary"><div class="admonitionHeading_Gvgb"><span class="admonitionIcon_Rf37"><svg viewBox="0 0 14 16" xmlns="http://www.w3.org/2000/svg"><path d="M6.3 5.69a.942.942 0 0 1-.28-.7c0-.28.09-.52.28-.7.19-.18.42-.28.7-.28.28 0 .52.09.7.28.18.19.28.42.28.7 0 .28-.09.52-.28.7a1 1 0 0 1-.7.3c-.28 0-.52-.11-.7-.3zM8 7.99c-.02-.25-.11-.48-.31-.69-.2-.19-.42-.3-.69-.31H6c-.27.02-.48.13-.69.31-.2.2-.3.44-.31.69h1v3c.02.27.11.5.31.69.2.2.42.31.69.31h1c.27 0 .48-.11.69-.31.2-.19.3-.42.31-.69H8V7.98v.01zM7 2.3c-3.14 0-5.7 2.54-5.7 5.68 0 3.14 2.56 5.7 5.7 5.7s5.7-2.55 5.7-5.7c0-3.15-2.56-5.69-5.7-5.69v.01zM7 .98c3.86 0 7 3.14 7 7s-3.14 7-7 7-7-3.12-7-7 3.14-7 7-7z" fill-rule="evenodd"></path></svg></span>note</div><div class="admonitionContent_BuS1"><p>You can follow the official liblab guide to <a href="https://liblab.com/docs/tutorials/ci-cd/integrate-with-github-actions#create-liblab-and-github-tokens" rel="noopener noreferrer" target="_blank">create both the GitHub and liblab tokens</a>.</p></div></div>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="step-by-step-from-api-change-to-updated-sdk">Step-by-Step: From API Change to Updated SDK<a class="hash-link" href="https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd#step-by-step-from-api-change-to-updated-sdk" title="Direct link to Step-by-Step: From API Change to Updated SDK">​</a></h2>
<p>Let's walk through a full cycle: from updating the API to seeing the new SDK generated and proposed as a pull request.</p>
<ol>
<li>
<p><strong>Make a Change to Your API and Push to <code>main</code></strong></p>
<p>In this example, we add support for Japanese to our "Hello World" API. Once the change is committed and pushed to the <code>main</code> branch, the CI/CD pipeline kicks off automatically.</p>
<div class="theme-admonition theme-admonition-note admonition_xJq3 alert alert--secondary"><div class="admonitionHeading_Gvgb"><span class="admonitionIcon_Rf37"><svg viewBox="0 0 14 16" xmlns="http://www.w3.org/2000/svg"><path d="M6.3 5.69a.942.942 0 0 1-.28-.7c0-.28.09-.52.28-.7.19-.18.42-.28.7-.28.28 0 .52.09.7.28.18.19.28.42.28.7 0 .28-.09.52-.28.7a1 1 0 0 1-.7.3c-.28 0-.52-.11-.7-.3zM8 7.99c-.02-.25-.11-.48-.31-.69-.2-.19-.42-.3-.69-.31H6c-.27.02-.48.13-.69.31-.2.2-.3.44-.31.69h1v3c.02.27.11.5.31.69.2.2.42.31.69.31h1c.27 0 .48-.11.69-.31.2-.19.3-.42.31-.69H8V7.98v.01zM7 2.3c-3.14 0-5.7 2.54-5.7 5.68 0 3.14 2.56 5.7 5.7 5.7s5.7-2.55 5.7-5.7c0-3.15-2.56-5.69-5.7-5.69v.01zM7 .98c3.86 0 7 3.14 7 7s-3.14 7-7 7-7-3.12-7-7 3.14-7 7-7z" fill-rule="evenodd"></path></svg></span>note</div><div class="admonitionContent_BuS1"><p>For the sake of simplicity, we're pushing the change directly to the <code>main</code> branch. In a real-world setup, you'd typically open a pull request, review it, and merge it to trigger the workflow.</p></div></div>

</li>
<li>
<p><strong>Deploy New API Version</strong></p>
<p>The <code>deploy-and-sync-sdk.yml</code> workflow runs on every push to <code>main</code>. In this case I've deployed the API to Render but you can use any hosting service.</p>
<p><img alt="deploy-new-api-version" class="img_ev3q" height="1788" src="https://liblab.com/assets/images/deploy-new-version-1eff7d6ca07dea742e7b92b84cf83932.png" width="3444" /></p>
</li>
<li>
<p>Sync SDK With API Changes</p>
<p>After deployment, the workflow fetches the live OpenAPI spec and compares it with the version stored in <code>sdk-control/api.json</code>.</p>
<p>If a change is detected:</p>
<ul>
<li><code>api.json</code> is updated and committed</li>
<li>The version is bumped in <code>liblab.config.json</code></li>
<li>A new SDK is built using <code>liblab build</code></li>
<li>Pull requests are created in the SDK repositories with the fresh SDKs. One PR in each repository for each programming language.</li>
</ul>
<p><img alt="sync-sdk-with-api-changes" class="img_ev3q" height="1948" src="https://liblab.com/assets/images/sync-sdk-with-api-changes-879d050d6eb09a4bb4a47aeeaef7db69.png" width="3498" /></p>
</li>
<li>
<p>Review the SDK Pull Request</p>
<p>The <code>hello-world-sdk-python</code> and <code>hello-world-sdk-typescript</code> repositories receive automatic pull requests with the updated SDK files. We can now review the changes before merging.</p>

</li>
<li>
<p>Merge the PR 🎉</p>
<p>Once the pull request is approved and merged, the new SDK version is ready to be published.</p>
<p>The entire loop - from API change to up-to-date SDK - runs without any manual steps.</p>
</li>
</ol>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="next-steps">Next Steps<a class="hash-link" href="https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd#next-steps" title="Direct link to Next Steps">​</a></h2>
<p>With this setup it's simple to automate the most critical part of your SDK lifecycle - keeping it in sync with your API. From here, you can take your CI/CD pipeline even further:</p>
<ul>
<li><strong>Publish to package managers</strong> - Automate releases to npm, PyPI, Maven, NuGet or other ecosystems so developers can consume updates without delays.</li>
<li><strong>Add automated testing</strong> - Validate that the generated SDK behaves correctly before it gets merged.</li>
<li><strong>Integrate Changelog generation</strong> - Include meaningful release notes for each SDK update.</li>
<li><strong>Set up notifications</strong> - Alert your team or community when new SDK versions are available.</li>
</ul>
<div class="theme-admonition theme-admonition-info admonition_xJq3 alert alert--info"><div class="admonitionHeading_Gvgb"><span class="admonitionIcon_Rf37"><svg viewBox="0 0 14 16" xmlns="http://www.w3.org/2000/svg"><path d="M7 2.3c3.14 0 5.7 2.56 5.7 5.7s-2.56 5.7-5.7 5.7A5.71 5.71 0 0 1 1.3 8c0-3.14 2.56-5.7 5.7-5.7zM7 1C3.14 1 0 4.14 0 8s3.14 7 7 7 7-3.14 7-7-3.14-7-7-7zm1 3H6v5h2V4zm0 6H6v2h2v-2z" fill-rule="evenodd"></path></svg></span>info</div><div class="admonitionContent_BuS1"><p>This blog post doesn't cover SDK publishing, but <a href="https://liblab.com/docs/tutorials/ci-cd/integrate-with-github-actions" rel="noopener noreferrer" target="_blank">this tutorial shows how to set up a full CI/CD pipeline, including publishing to package managers.</a></p></div></div>
<h2 class="anchor anchorWithStickyNavbar_LWe7" id="conclusion">Conclusion<a class="hash-link" href="https://liblab.com/blog/automatically-sync-your-sdk-with-ci-cd#conclusion" title="Direct link to Conclusion">​</a></h2>
<p>Automating SDK generation with CI/CD not only saves time, it also improves reliability and developer experience. By integrating liblab into your pipeline, you ensure your SDKs stay up to date with every API change - without any manual work. Set it up once, and let your workflow handle the rest.</p>
