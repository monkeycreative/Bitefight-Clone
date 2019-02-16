###### SignariusCaro - Browsergame
## Online Role Playing Game

![Image](src)

BUILD STATUS

### Table of Contents
1. [Requirements](#requirements)
2. [Installation](#installation)
3. [Running in local enviroment](#running-in-local-enviroment)
4. [License](#license)


### Requirements (for Local Development)
* PHP 7.0.0 or Higher
* Git
* Composer
* SQLite


### Installation
* Clone the Repo
	```markdown
	git clone https://github.com/monkeycreative/SignariusCaro.git release
	```
	
* Navigate to the Project folder
	```markdown
	cd signariuscaro
	```
	
* Create .env file from the .env.example file
	On Windows:
	```markdown
	copy .env.example .env
	```
	On Linux/Debian:
	```markdown
	cp .env.example .env
	```

* Run composer install to import the dependencies and enable auto-loading
	```markdown
	composer install
	```
	
* Generate Laravel Application key
	```markdown
	php artisan key:generate
	```
	
* Create SQLite database file
	On Windows:
	```markdown
	copy NUL database\database.sqlite
	```
	On Linux/Debian:
	```markdown
	touch database/database.sqlite
	```
	
* Run Laravel database migration and seeds
	```markdown
	php artisan migrate --seed
	```
	
### Running in local enviroment
* Create a symbolic link from "public/storage" to "storage/app/public"
	```markdown
	php artisan storage:link
	```
	
* Run PHP build-in development server on the host machine
	```markdown
	php artisan serve
	```

* Navigate to http://localhost:8000/

* Enable Laravel Tast Scheduling
	1. Open the cron tab file
		```markdown
		crontab -e
		```
	2. Add the following line and save
		On Windows:
		Open the Terminal as Administrator, navigate to the project`s folder and run:
		```markdown
		schtasks /create /sc minute /mo 1 /tn "RPG SCHEDULER" /tr %cd%\scheduler.bat
		```
		On Linux/Debian:
		```markdown
		***** php <path-to-project>/artisan schedule:run >> /dev/null 2>&1
		```
		
	To Disable the annoying command-line-pop-up each time the task runs:
	
		* Open Windows "**_Run_**" dialog by pressing "_Windows Key_ + _r_"
		* Enter type "_Taskschd.msc_" and press _Enter_. This will open the "*Task Scheduler*".
		* In *Task Scheduler`s* "_Active Tasks_" section find the "*_SignariusCaro SCHEDULER_*" task and _double-click_ it.
		* In the left "*_Actions_*" panel click "_Properties_". This will open "*Properties*" pop-up.
		* In the pop-up select the "*_Run whether user is logged in or not_*" and press _Enter_. You maybe asked for your 			   Windows user's password to complete the process.
		
	
	To Remove the scheduled task you can use
		```markdown
		schtask /delete /tn "SignariusCaro SCHEDULER" /f
		```
		
	### License
	Open-sourced software licensed under the [MIT-LICENSE](http://opensource.org/licenses/MIT)
