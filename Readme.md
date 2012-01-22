
# Connect Form

Connect Form is a multipart / urlencoded form parsing middleware utilizing [node-formidable](http://github.com/felixge/node-formidable) behind the scenes.

## Installation

via npm:

	$ npm install connect-form-sync

## Example

checkout https://github.com/anatoliychakkaev/railway-example-upload

    files_controller.js:

    action('create', function () {
        this.file = new File();
        var tmpFile = req.form.files.file;
        this.file.upload(tmpFile.name, tmpFile.path, function (err) {
            if (err) {
                console.log(err);
                this.title = 'New file';
                flash('error', 'File can not be created');
                render('new');
            } else {
                flash('info', 'File created');
                redirect(path_to.files);
            }
        }.bind(this));
    });
