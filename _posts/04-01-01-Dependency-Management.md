# Gerenciamento de Dependência

There are a ton of PHP libraries, frameworks, and components to choose from. Your project will likely use several of them — these are project dependencies. Until recently, PHP did not have a good way to manage these project dependencies. Even if you managed them manually, you still had to worry about autoloaders. No more.

Currently there are two major package management systems for PHP - Composer and PEAR. Which one is right for you? The answer is both.

 * Use **Composer** when managing dependencies for a single project.
 * Use **PEAR** when managing dependencies for PHP as a whole on your system.

In general, Composer packages will be available only in the projects that you explicitly specify whereas a PEAR package would be available to all of your PHP projects. While PEAR might sound like the easier approach at first glance, there are advantages to using a project-by-project approach to your dependencies.
Há toneladas de bibliotecas PHP, frameworks, e componentes para você escolher. Seu projeto provavelmente irá usar muitos deles - estes são as dependências do projeto. Até recentemente, PHP não possuia uma boa forma de gerenciar estas dependências do projeto. Se você gerenciasse elas manualmente, ainda assim teria que se preocupar com autoloaders. Não mais.