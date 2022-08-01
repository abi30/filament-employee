create project
composer require breeze 
install ->breeze 
composer require filament 
create database
php artisan filament: user 
create user 


Eployees Management

-----On SideBar-----
--|dachboard

--|Employees Management

--|System Managemnt
   *Country
   *state
   *City
   *Department

--|UserManagement
   *user
 


Authentication:
-user will be able to login using email and password
-tree failed attempt will lock the user for 5 min
 
user Management:
-create Update and Dalete Users
-change Password
Search Users by User name and email

employee Management:
-List of emplyees with search and filter by name and department
-Create Update by User Name and email

System Management:

 *Country:
	-List Countries with Search
	-Create Update and delete
 *State:
	-List States with Search
	-Create Update and delete
 *City:
	-List Cities with Search
	-Create Update and delete

 *DepartMent:
	-List States with Search
	-Create Update and delete



Create Api endPoint to list all employees order alphabetically by last name





 

 Migration_Employees
Schema::create('employees', function (Blueprint $table) {
            $table->id();
            $table->string('last_name');
            $table->string('first_name');
            $table->string('middle_name')->nullable();
            $table->string('address');
            $table->foreignId('department_id')->constrained();
            $table->foreignId('country_id')->constrained();
            $table->foreignId('state_id')->constrained();
            $table->foreignId('city_id')->constrained();
            $table->char('zip_code');
            $table->date('birthdate')->nullable();
            $table->date('date_hired')->nullable();
            $table->timestamps();
        });

 Migration_Countries
  Schema::create('countries', function (Blueprint $table) {
            $table->id();
            $table->char('country_code');
            $table->string('name');
            $table->timestamps();
        });
 Migration_States
  Schema::create('states', function (Blueprint $table) {
            $table->id();
            $table->foreignId('country_id')->constrained();
            $table->string('name');
            $table->timestamps();
        });
 Migration_Cities
  Schema::create('cities', function (Blueprint $table) {
            $table->id();
            $table->foreignId('state_id')->constrained();
            $table->string('name');
            $table->timestamps();
        });

 Migration_Departments
  Schema::create('departments', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->timestamps();
        });
 Migration_Users
   Schema::create('users', function (Blueprint $table) {
              $table->id();
            $table->string('username');
            $table->string('last_name');
            $table->string('first_name');
            $table->string('email')->unique();
            $table->timestamp('email_verified_at')->nullable();
            $table->string('password');
            $table->rememberToken();
            $table->timestamps();
        });


4. Create Country Resource
-create country Resource
-create the form
-crate teh table

php artisan make:filament-resource Country