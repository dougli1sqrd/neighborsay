# neighborsay
Mr Rogers Quotation Fortune file

`neighborhood` and `neighborhood.dat` go together as a new fortune file for the BSD `fortune` program. These are quotes from Fred Rogers either in the  show Mr. Roger's Neighborhood or from speeches. With `fortune` the terminal can pick one of the quotes at random to print to the screen in an uplifting manner:

    I hope you're proud of yourself for the times you've said 'yes,' when all it meant was extra work for you and was seemingly helpful only to somebody else.
  
Combined with `cowsay` you can have an animal or other character say a Mr. Rogers uplifting quote. 

## Installation
1. Install `cowsay` and `fortune`

    apt-get install cowsay
    apt-get install fortune
    
2. Place the two neighborhood files (`neighborhood` and `neighborhood.dat`) in an accessible location, probably within your home directory somewhere. I placed mine in a new folder called `config`

    mkdir ~/config
    cp ~/neighborsay/neighbor* ~/config/

3. Make sure it works:

    fortune config/neighborhood | cowsay -f moose
    / I hope you're proud of yourself for the \
    | times you've said 'yes,' when all it    |
    | meant was extra work for you and was    |
    | seemingly helpful only to somebody      |
    \ else.                                   /
    -----------------------------------------
      \
       \   \_\_    _/_/
        \      \__/
               (oo)\_______
               (__)\       )\/\
                   ||----w |
                   ||     ||


4. You can place this command in your `~/.bashrc` so that when a new terminal is opened a Mr. Rogers fortune appears. At the very bottom of the `~/.bashrc` file, place:

    fortune $HOME/config/neighborhood | cowsay -f moose
    
Test by opening a new terminal. 

## Generating the .dat file:
Your fortune file should be a series of strings separated by lines that only contain the percent sign `%`. In this example we'll say the fortunes file here will be called `neighborhood`.

    I hope you're proud of yourself for the times you've said 'yes,' when all it meant was extra work for you and was seemingly helpful only to somebody else.
    %
    It takes strength to acknowledge our anger, and sometimes more strength yet to curb the aggressive urges anger may bring and to channel them into nonviolent outlets.
    %
    ...
    
Then, run the command:

    strfile -c % neighborhood neighborhood.dat
    
It appears that both the raw text and .dat files need to be in the same directory to be seen by fortune. 
