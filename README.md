Lua GDB Helpers
===============

This is a collection of several GDB macros that simplify debugging of C modules for Lua. Lua has to be compiled with debugging symbols, or the appropriate "dbg" package (i.e. `liblua5.1-0-dbg` in Debian/Ubuntu) needs to be installed.

Installation & Running
----------------------

Copy the `luagdb.txt` file somewhere - installation complete.

To include the macros into your GDB session, run the following command:

    source <path to luagdb.txt>

It is advisable to include the line into your `~/.gdbinit` file (see the [GDB documentation](http://sourceware.org/gdb/current/onlinedocs/gdb/Startup.html)), so you do not have to type the command everytime you start GDB.

Reference
---------

- luastack [L] - lists the values on the current Lua C stack. By default, uses the current variable `L` as the `lua_State` pointer, however, an alternate `lua_State` can be provided as the first argument if needed.

- luaprint < value > [verbose] - Pretty-prints a `TValue` passed as argument. Expects a pointer to a `TValue`. When verbose is 1, expands tables, metatables and userdata environments.

- luaprinttable < table > - Pretty-prints a Lua Table. Expects a pointer to `Table`.

- luavalue < index > [L] - Provides a pointer to a TValue from a stack index. By default, uses the current variable L as a lua_State pointer, but can be specified as the second argument. The return value is passed in variable $obj.

However, note that "pretty-printing" is not as pretty as it could be. First, the hash part is displayed, then the array part. Entries in hash part are separated by newlines, the ones in array part are displayed side-by-side.

License
-------
Copyright (c) 2010 Michal Kottman, MIT License
