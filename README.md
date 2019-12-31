#WordPress Alpha Color Picker #
 
 If we want extra version of wordpress color settings color such as tranparency, RGB color. It is used for it. 

### Install
To install include alpha-color-picker.php file in the root of your theme or plugins in customizer.php file.

```php
require get_template_directory() . '/alpha-color-picker.php';
```


### Usage

Add this code in your theme or plugin's customizer.php file:

```php
function xxx_customize_register( $wp_customize ) {

    if( class_exists('PostMag_Customize_Alpha_Color_Control'){
        // Alpha Color Picker setting.
        $wp_customize->add_setting(
            'alpha_color_setting',
            array(
                'default'     => 'rgba(209,0,55,0.7)',
                'type'        => 'theme_mod',
                'capability'  => 'edit_theme_options',
                'transport'   => 'postMessage'
            )
        );
    
        // Alpha Color Picker control.
        $wp_customize->add_control(
            new PostMag_Customize_Alpha_Color_Control(
                $wp_customize,
                'alpha_color_control',
                array(
                    'label'         => __( 'Alpha Color Picker', 'yourtextdomain' ),
                    'section'       => 'colors',
                    'settings'      => 'alpha_color_setting',
                    'show_opacity'  => true, // Optional.
                    'palette'	=> array(
                        'rgb(150, 50, 220)', // RGB, RGBa, and hex values supported
                        'rgba(50,50,50,0.8)',
                        'rgba( 255, 255, 255, 0.2 )', // Different spacing = no problem
                        '#00CC99' // Mix of color types = no problem
                    )
                )
            )
        );
    }
}
add_action( 'customize_register', 'xxx_customize_register' );
```

### More Information ###

More detailed usage information [here](http://postmagthemes.com/alpha-color-picker-control-for-the-wordpress-customizer/).

Feedback and pull requests are encouraged!

### Contribute

You can make this better by contributing. If you find a bug or simply want to contribute to this collection, submit your pull request and we'll have a look on it. 