# Lab 1: Introduction to Distributed Databases 


## Download the binary

The CockroachDB binary for Linux requires `glibc`, `libncurses`, and
`tzdata`, which are found by default on nearly all Linux distributions,
with Alpine as the notable exception.

1.  Download the CockroachDB v23.1.13 archive as shown below. 
    The archive contains the `cockroach` binary and the supporting
    libraries that are used to provide `spatial features`.
    Extract the archive and optionally copy the `cockroach` binary into
    your `PATH` so you can execute cockroach commands from any shell. 
    If you get a permission error, use `sudo`.

    ```
    cd ~/Desktop/
    
    wget https://binaries.cockroachdb.com/cockroach-v23.1.13.linux-amd64.tgz

    tar -xvzf cockroach-v23.1.13.linux-amd64.tgz 

    cd cockroach-v23.1.13.linux-amd64

    cp -i cockroach /usr/local/bin
    ```

2.  CockroachDB uses custom-built versions of the `GEOS`
    libraries. Copy these libraries to one of the locations where
    CockroachDB expects to find them.

    By default, CockroachDB looks for external libraries in
    `/usr/local/lib/cockroach` or a `lib` subdirectory of the
    CockroachDB binary\'s current directory. 
    The instructions below uses the `/usr/local/lib/cockroach` location.

    1.  Create the directory where the external libraries will be
        stored:

        ```
        mkdir -p /usr/local/lib/cockroach
        ```

    2.  Copy the library files to the directory:

        ```
        cp -i cockroach-v23.1.13.linux-amd64/lib/libgeos.so /usr/local/lib/cockroach/

        cp -i cockroach-v23.1.13.linux-amd64/lib/libgeos_c.so /usr/local/lib/cockroach/
        ```

        If you get a permissions error, prefix the command with `sudo`.

3.  Verify that CockroachDB can execute spatial queries.

    1.  Make sure the `cockroach` binary you just installed is the one
        that runs when you type `cockroach` in your shell:


        ```
        which cockroach
        ```

        ```
        /usr/local/bin/cockroach
        ```

    2.  Start a temporary, in-memory cluster using `cockroach demo`:


        ```
        cockroach demo
        ```

    3.  In the demo cluster\'s interactive SQL shell, run the following
        command to test that the spatial libraries have loaded properly:



        ```
        SELECT ST_IsValid(ST_MakePoint(1,2));
        ```

        You should see the following output:

        ```
          st_isvalid
        --------------
        true
        (1 row)
        ```

        If your `cockroach` binary is not properly accessing the
        dynamically linked C libraries in `/usr/local/lib/cockroach`, it
        will output an error message like the one below.

        ```
        ERROR: st_isvalid(): geos: error during GEOS init: geos: cannot load GEOS from dir "/usr/local/lib/cockroach": failed to execute dlopen
                  Failed running "sql"
        ```
