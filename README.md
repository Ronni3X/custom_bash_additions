# custom_bash_additions
useful bash customizations

# customized up directory completion
added the following lines to the _cd completion function (almost at the top of the function) within the bash_completion file:

    \#catch custom numbered up directory option
    if [[ $cur =~ ^\.\.[0-9]+$ ]]; then
        local back="../"
        local num=$(echo "$cur" | cut -f 3 -d ".");
        cur=""
        for ((l=1;l<=$num;l++)); do cur=$cur$back; done;
        _filedir -d
        return
    fi

This if statement allows you to cd up a specific number of times using the following format:

cd ..3

The above will be converted to:

cd ../../../

when you press tab. You can then press <tab><tab> to see the directories within that back directory and continue to tab complete.
    
