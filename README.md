# Heroku Buildpack for Haskell modified for MFlow demos. 

It add monadloc-pp and cpphs executables that are necessary for compiling MFlow and/or the MFlow demos.

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for Haskell apps. It uses GHC 7.4.1 and cabal-1.16.0.1.


## Usage

Use anvil to allow largue compilations:

    $ ls
    Procfile app.cabal src

    $ heroku apps:create instance-name 


    $ heroku plugins:install https://github.com/ddollar/heroku-anvil

    $ heroku build -r -b https://github.com/agocorona/heroku-buildpack-haskell.git

    -----> Heroku receiving push
    -----> Fetching custom git buildpack... done
    -----> Haskell app detected
    -----> Downloading GHC
    ######################################################################## 100.0%
    -----> Downloading Cabal
    ######################################################################## 100.0%
    -----> Setting up ghc-pkg
    ...





