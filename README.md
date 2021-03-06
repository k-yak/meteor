# Meteor for raspberry

Meteor is an ultra-simple environment for building modern web
applications.

With Meteor you write apps:

* in pure JavaScript
* that send data over the wire, rather than HTML
* using your choice of popular open-source libraries

Documentation is available at http://docs.meteor.com/

## Prerequisites
Install nodejs:

    wget http://node-arm.herokuapp.com/node_latest_armhf.deb
    sudo dpkg -i node_latest_armhf.deb
    
Install mongoDb:

* tutorial from : http://raspbian-france.fr/installer-mongodb-raspberry-pi/ (french)

Install:

    sudo -s
    cd
    wget http://raspbian-france.fr/download/mongodb-rpi_20140207.zip
    adduser --firstuid 100 --ingroup nogroup --shell /etc/false --disabled-password --gecos "" --no-create-home mongodb
    unzip mongodb-rpi_20140207.zip
    cp -R mongodb-rpi/mongo /opt
    chmod +x /opt/mongo/bin/*
    mkdir /var/log/mongodb
    chown mongodb:nogroup /var/log/mongodb
    mkdir /var/lib/mongodb
    chown mongodb:nogroup /var/lib/mongodb
    cp mongodb-rpi/debian/init.d /etc/init.d/mongod
    cp mongodb-rpi/debian/mongodb.conf /etc/
    ln -s /opt/mongo/bin/mongod /usr/bin/mongod
    chmod u+x /etc/init.d/mongod
    update-rc.d mongod defaults /etc/init.d/mongod start
    su pi
    
## Meteor install

If you want to run on the bleeding edge, or help develop Meteor, you
can run Meteor directly from a git checkout.

    git clone git://github.com/k-yak/meteor.git
    cd meteor
    ./scripts/generate-dev-bundle.sh

Now you can run meteor directly from the checkout 

    ./meteor

From your checkout, you can read the docs locally. The `/docs` directory is a
meteor application, so simply change into the `/docs` directory and launch
the app:

    cd docs/
    ../meteor

You'll then be able to read the docs locally in your browser at
`http://localhost:3000/`.

Note that if you run Meteor from a git checkout, you cannot pin apps to specific
Meteor releases or run using different Meteor releases using `--release`.

## Uninstalling Meteor

Aside from a short launcher shell script, Meteor installs itself inside your
home directory. To uninstall Meteor, run:

    rm -rf ~/.meteor/
    sudo rm /usr/local/bin/meteor

## Developer Resources

Building an application with Meteor?

* Announcement list: sign up at http://www.meteor.com/
* Ask a question: http://stackoverflow.com/questions/tagged/meteor
* Meteor help and discussion mailing list: https://groups.google.com/group/meteor-talk
* IRC: `#meteor` on `irc.freenode.net`

Interested in contributing to Meteor?

* Core framework design mailing list: https://groups.google.com/group/meteor-core
* Contribution guidelines: https://github.com/meteor/meteor/tree/devel/Contributing.md

We are hiring!  Visit https://www.meteor.com/jobs to
learn more about working full-time on the Meteor project.
