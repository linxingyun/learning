

<h3> Command usage </h3>
<ul>
<li>svn add all dir setting </li>

'''

    This will add all unknown (except ignored) files under the specified directory tree:

        svn add --force path/to/dir
    This will add all unknown (except ignored) files in the current directory and below:

        svn add --force .

'''

<li>svn ignore dir setting: </li>

'''

    Use:

    cat > ignorelist << END
    file1
    file2
    file3
    END

    svn propset svn:ignore -F ignorelist dir1
    Or without an external file, and assuming you're on Linux or a system with /dev/fd:

    svn propset svn:ignore -F /dev/fd/0 dir1 << END
    file1
    file2
    file3
    END
    
'''

</ul>
