
github UncleReaton pipex : https://codeberg.org/UncleReaton/pipex/src/branch/main/src/main.c

main.c

```js
#include "../headers/pipex.h"

int	main(int ac, char **av, char **env)
{
	int	infile;
	int	outfile;

	if (ac != 5)
		return (error_calling_pipex());
	if (!check_existence(av[1]))
		return (error_infile(av[1]));
	infile = open(av[1], O_RDONLY);
	outfile = open(av[4], O_CREAT | O_RDWR | O_TRUNC, 0644);
	if (infile < 0 || outfile < 0)
		return (EXIT_FAILURE);
	pipex(infile, outfile, av, env);
	return (EXIT_SUCCESS);
}
```


