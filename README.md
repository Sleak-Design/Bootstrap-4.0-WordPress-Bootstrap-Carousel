# Bootstrap-4.0-WordPress-Bootstrap-Carousel

/*
Plugin Name:  Bootstrap4_wordpress_carousel
Plugin URI:   https://developer.wordpress.org/sleakdesign
Description:  Sleak Design Simple Start For Bootstrap 4.0 Carousel
Version:      1
Author:       Sleak design'S Sidney Malone
Author URI:   https://developer.wordpress.org/sleakdesign
License:      GPL2
License URI:  https://www.gnu.org/licenses/gpl-2.0.html
Text Domain:  
Domain Path:  /languages
*/

function sleak_scripts() {
// Registering Bootstrap style
wp_enqueue_style( 'bootstrap_min', get_stylesheet_directory_uri().'/css/bootstrap.min.css' );

wp_enqueue_style( 'bootstrap_min', get_stylesheet_directory_uri().'/css/styles.css' );

wp_enqueue_script('jquery');
//Registering Bootstrap Script
wp_enqueue_script( 'bootstrap_min', get_template_directory_uri() . '/js/bootstrap.min.js', array(), '', true );
}
add_action( 'wp_enqueue_scripts', 'sleak_scripts' );
add_action( 'init', 'custom_bootstrap_slider' );


function custom_bootstrap_slider() {
	$labels = array(
		'name'               => _x( 'Slider', 'post type general name'),
		'singular_name'      => _x( 'Slide', 'post type singular name'),
		'menu_name'          => _x( 'Bootstrap 4 Slider', 'admin menu'),
		'name_admin_bar'     => _x( 'Slide', 'add new on admin bar'),
		'add_new'            => _x( 'Add New', 'Slide'),
		'add_new_item'       => __( 'Name'),
		'new_item'           => __( 'New Slide'),
		'edit_item'          => __( 'Edit Slide'),
		'view_item'          => __( 'View Slide'),
		'all_items'          => __( 'All Slide'),
		'featured_image'     => __( 'Featured Image', 'text_domain' ),
		'search_items'       => __( 'Search Slide'),
		'parent_item_colon'  => __( 'Parent Slide:'),
		'not_found'          => __( 'No Slide found.'),
		'not_found_in_trash' => __( 'No Slide found in Trash.'),
	);

	$args = array(
		'labels'             => $labels,
		'menu_icon'	     => 'dashicons-star-half',
    	        'description'        => __( 'Description.'),
		'public'             => true,
		'publicly_queryable' => true,
		'show_ui'            => true,
		'show_in_menu'       => true,
		'query_var'          => true,
		'rewrite'            => true,
		'capability_type'    => 'post',
		'has_archive'        => true,
		'hierarchical'       => true,
		'menu_position'      => null,
		'susleakorts'           => array('title','editor','thumbnail')
	);

	register_post_type( 'slider', $args );
}



For output in template file :
 
 <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
        <ol class="carousel-indicators">
          <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
          <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
          <li data-target="#carouselExampleIndicators" data-slide-to="2"></li>
        </ol>
		 <!-- Wrapper for slides -->
		<div class="carousel-inner" role="listbox">
		<?php $slider = get_posts(array('post_type' => 'slider', 'posts_per_page' => 5)); ?>
		  <?php $count = 0; ?>
		  <?php foreach($slider as $slide): ?>
		  <div class="carousel-item <?php echo ($count == 0) ? 'active' : ''; ?>">
			<img src="<?php echo wp_get_attachment_url( get_post_thumbnail_id($slide->ID)) ?>" class="img-fluid"/>
		  </div>
		  <?php $count++; ?>
		<?php endforeach; ?>
		</div>

        <a class="carousel-control-prev" href="#carouselExampleIndicators" role="button" data-slide="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="sr-only">Previous</span>
        </a>
        <a class="carousel-control-next" href="#carouselExampleIndicators" role="button" data-slide="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="sr-only">Next</span>
        </a>
      </div>
