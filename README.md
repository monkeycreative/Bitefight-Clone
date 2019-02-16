###### SignariusCaro - Browsergame
## Online Role Playing Game

![Image](src)

BUILD STATUS

### Table of Contents
1. Requirements
2. Installation
3. Running in local enviroment
4. License


### Requirements (for Local Development)
..* PHP 7.0.0 or Higher
..* Git
..* Composer
..* SQLite


### Installation
..* Clone the Repo
	```
	git clone https://github.com/monkeycreative/SignariusCaro.git release
	```
	
..* Navigate to the Project folder
	```
	cd signariuscaro
	```
	
..* Create .env file from the .env.example file
	On Windows:
	```
	copy .env.example .env
	```
	On Linux/Debian:
	```
	cp .env.example .env
	```

..* Run composer install to import the dependencies and enable auto-loading
	```
	composer install
	```
	
..* Generate Laravel Application key
	```
	php artisan key:generate
	```
	
..* Create SQLite database file
	On Windows:
	```
	copy NUL database\database.sqlite
	```
	On Linux/Debian:
	```
	touch database/database.sqlite
	```
	
..* Run Laravel database migration and seeds
	```
	php artisan migrate --seed
	```
	
### Running in local enviroment
..* Create a symbolic link from "public/storage" to "storage/app/public"
	```
	php artisan storage:link
	```
	
..* Run PHP build-in development server on the host machine
	```
	php artisan serve
	```

..* Navigate to http://localhost:8000/

..* Enable Laravel Tast Scheduling
	1. Open the cron tab file
		```
		crontab -e
		```
	2. Add the following line and save
		On Windows:
		Open the Terminal as Administrator, navigate to the project`s folder and run:
		```
		schtasks /create /sc minute /mo 1 /tn "RPG SCHEDULER" /tr %cd%\scheduler.bat
		```
		On Linux/Debian:
		```
		***** php <path-to-project>/artisan schedule:run >> /dev/null 2>&1
		```
		
	To Disable the annoying command-line-pop-up each time the task runs:
		
		1. Open Windows "*_Run_*" dialog by pressing "_Windows Key_ + _r_"
		2. Enter type "_Taskschd.msc_" and press _Enter_. This will open the "*Task Scheduler*".
		3. In *Task Scheduler`s* "_Active Tasks_" section find the "*_SignariusCaro SCHEDULER_*" task and _double-click_ it.
		4. In the left "*_Actions_*" panel click "_Properties_". This will open "*Properties*" pop-up.
		5. In the pop-up select the "*_Run whether user is logged in or not_*" and press _Enter_. You maybe asked for your Windows user's password to complete the process.
		
	
	To Remove the scheduled task you can use
		```
		schtask /delete /tn "SignariusCaro SCHEDULER" /f
		
		
	### License
	Open-sourced software licensed under the [MIT-LICENSE](http://opensource.org/licenses/MIT)
