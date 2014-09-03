# Heroku Buildpack for Haskell modified to install GHC and Haste 
in the running environment so that Haste programs can be build and run.

It is used to install heroku instances of the [tryhplay](http://github.com/agocorona/tryhplay) project


This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for Haskell apps. It uses GHC 7.4.1 and cabal-1.16.0.1.


## Usage

Use anvil to allow largue compilations:

    $ ls
    Procfile app.cabal src

    $ heroku apps:create instance-name 


    $ heroku plugins:install https://github.com/ddollar/heroku-anvil

    $ heroku build -r -b https://github.com/agocorona/heroku-buildpack-haste.git

    -----> Heroku receiving push
    -----> Fetching custom git buildpack... done
    -----> Haskell app detected
    -----> Downloading GHC
    ######################################################################## 100.0%
    -----> Downloading Cabal
    ######################################################################## 100.0%
    -----> Setting up ghc-pkg
    ...


TT set the PATH environment. Run this in the console:

    $ heroku config:set PATH=/app/ghc/bin:/app/.cabal/bin:/app/bin:/app/node_modules/.bin:node_modules/.bin:/app/bin:/app/node_modules/.bin:/usr/local/bin:/usr/bin:/bin 


then you can invoke ghc, cabal, hastec, haste-inst etc from your web application.
