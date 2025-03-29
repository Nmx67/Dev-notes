<header>

<!--
  <<< Author notes: Course header >>>
  Include a 1280×640 image, course title in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Add your open source license, GitHub uses MIT license.
-->

# Install conan on windows

Thanks : https://www.and-fs.de/posts/conan/install-in-venv/
_Default pip install will install conan in an obscure scripts path._

</header>

<!--
  <<< Author notes: Step 1 >>>
  Choose 3-5 steps for your course.
  The first step is always the hardest, so pick something easy!
  Link to docs.github.com for further explanations.
  Encourage users to open new tabs for steps!
-->

Create a virtual environment in a globally accessible location, for instance %ProgramData% (i.e. C:\ProgramData).
> python -m venv %ProgramData%\.venv-conan

After that you can either activate the new environment and continue working in it, or you can use the Python executables inside the Scripts folder of the virtual environmen directly:

> %ProgramData%\.venv-conan\Scripts\pip install conan==2.*

At least create a symbolic link to the conan executable inside the virtual environments Scripts folder and place it into a location which is inside your systems search %PATH%.

Another solution can be adding %ProgramData%\.venv-conan\Scripts to %PATH%, but that can cause accidentially using the other executables placed there (such as python or pip).
Best practice is to have a system wide available folder which contains such links, for instance in %ProgramData%\links and to add this folder to your %PATH%.

> mkdir %ProgramData%\links
> mklink %ProgramData%\links\conan.exe %ProgramData%\.venv-conan\Scripts\conan.exe
> set PATH=%PATH%;%ProgramData%\links
> conan --version
Conan version 2.14.0

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/github-pages) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2023 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
