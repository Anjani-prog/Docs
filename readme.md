#### FCM-Django


### Setup ###

1.create a folder fcm-django
2.create env & activate
   #python3.6 -m venv env
   #source ./venv/bin/activate
3.$ pip install django
4.$ django-admin startproject testsite
5.$ pip install fcm-django   
  
   ##edit settings.py
    
     INSTALLED_APPS = (
        ...
       ### "rest_framework",
        "fcm_django"
       )
6. Create Project in firbase  (https://docs.kii.com/en/samples/push-notifications/push-notifications-android-fcm/create-project/)
   server key - Accessible under the Firebase > Project > Settings > Cloud Messaging tab.
   add this server key in settings.py

      FCM_DJANGO_SETTINGS = {
        "FCM_SERVER_KEY": "AAAAypKpF3M:APA91bHOD5j8kLBQ4uoP-w4oKEdHpVJR5_1BAAN-WtdpUyYeKlnEtlcY4kx1PrHVsPrFMbntf0Q66I
                      -oKlvz0RB1FYev-RYdLIv2ZlayB-Lhgmq84UnrDIexxhBkL7jojGFMxNZetYLn"
        }
7.in urls.py

        from django.conf.urls import url, include
	from fcm_django.api.rest_framework import FCMDeviceViewSet, FCMDeviceAuthorizedViewSet
	from rest_framework.routers import DefaultRouter

	router = DefaultRouter()
	router.register(r'devices', FCMDeviceViewSet)

	urlpatterns = [
	    url(r'^admin/', admin.site.urls),
	    url(r'^', include(router.urls)),
	]
8. run database migrations with python manage.py migrate
9. create Django administrator with python manage.py createsuperuser
10.collect static files with python manage.py collectstatic
11.run server with python manage.py runserver.


### to test ###
 
1.open http://localhost:8000/ and add device information
   --------- FCMDevice model fields ------------
	1- *registration_id (required - is FCM token)
	2- name (optional)
	3- active (default: true)
	4- user (optional)
	5- device_id (optional - can be used to uniquely identify devices)
	6- *type ('android', 'web', 'ios')

    registration id = > Device FCM token (Android/Emulator token)
	
2.add above information & send yourself a test notification with django admin actions
   shell example (run python manage.py shell from fcm-django/testsite):
   from fcm_django.models import FCMDevice
   device = FCMDevice.objects.all().first()
   device.send_message(title='title', body='message')
 
