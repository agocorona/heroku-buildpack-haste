# Heroku Buildpack for Haskell modified to install GHC and Haste 
in the running environment so that your web application can invoke  GHC and Haste  to build and run programs at exploitation time.

It is used to install heroku instances of the [tryhplay](http://github.com/agocorona/tryhplay) project


This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks)
for Haskell apps. It uses GHC 7.4.1 and cabal-1.16.0.1.


## Usage

Use a linux box. Don´t do this under windows. it does not work.

Your project need at least these files:

    $ ls
    Procfile app.cabal src

Create your heroku instance: (previously sign in and download the heroku soft: http://heroku.com)

    $ heroku apps:create instance-name 

install anvil to allow large compilations:

    $ heroku plugins:install https://github.com/ddollar/heroku-anvil

Build and release your project:

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


Set the PATH environment. Run this in the console:

    $ heroku config:set PATH=/app/ghc/bin:/app/.cabal/bin:/app/bin:/app/node_modules/.bin:node_modules/.bin:/app/bin:/app/node_modules/.bin:/usr/local/bin:/usr/bin:/bin 


Then you can invoke ghc, cabal, hastec, haste-inst etc from your web application.
