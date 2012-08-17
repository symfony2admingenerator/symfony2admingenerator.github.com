---
layout: cheat-sheet
title: Admingenerator cheat sheat for config.yml
---

# The config.yml

<ul>
	<li>
		<span class="code">admingenerator_generator:</span>
		<span class="doc"></span>
		<ul>
			<li>
				<span class="code">use_doctrine_orm: <span class="default_value">false</span> <span class="accepted_values">boolean</span></span>
				<span class="doc">Set true to activate generator services for doctrine orm</span>
			</li>
			<li>
				<span class="code">use_doctrine_odm: <span class="default_value">false</span> <span class="accepted_values">boolean</span></span>
				<span class="doc">Set true to activate generator services for doctrine odm</span>
			</li>
			<li>
				<span class="code">use_propel: <span class="default_value">false</span> <span class="accepted_values">boolean</span></span>
				<span class="doc">Set true to activate generator services for propel orm</span>
			</li>
			<li>
				<span class="code">overwrite_if_exists: <span class="default_value">false</span> <span class="accepted_values">boolean</span></span>
				<span class="doc">Set true when you create generator template to ensure rebuild on each call, by default admin is rebuilt when generator.yml change</span>
			</li>
			<li>
				<span class="code">base_admin_template: <span class="default_value">AdmingeneratorOldThemeBundle::base_admin.html.twig</span> <span class="accepted_values">Twig path</span></span>
				<span class="doc">Choose the base template for your admin </span>
			</li>
			<li>
				<span class="code">knp_menu_class: <span class="default_value">Admingenerator\GeneratorBundle\Menu\DefaultMenuBuilder</span> <span class="accepted_values">Class path</span></span>
				<span class="doc">Config of the KnpMenu</span>
			</li>
			<li>
				<span class="code">twig:</span>
				<span class="doc"></span>
				<ul>
					<li>
						<span class="code">use_localized_date: <span class="default_value">false</span> <span class="accepted_values">boolean</span></span>
						<span class="doc">Use twig filter `|localizeddate` instead of `|date` in lists for date and date time fields require php-intl</span>
					</li>
					<li>
						<span class="code">date_format: <span class="default_value">Y-m-d</span> <span class="accepted_values">string</span></span>
						<span class="doc">The date format givent to `|date` twig filter</span>
					</li>
					<li>
						<span class="code">datetime_format: <span class="default_value">Y-m-d H:i:s</span> <span class="accepted_values">string</span></span>
						<span class="doc">The datetime format givent to `|date` twig filter</span>
					</li>
					<li>
						<span class="code">localized_date_format: <span class="default_value">medium</span> <span class="accepted_values">short, medium, full</span></span>
						<span class="doc">The date format givent to `|localizeddate` twig filter</span>
					</li>
					<li>
						<span class="code">localized_datetime_format: <span class="default_value">medium</span> <span class="accepted_values">short, medium, full</span></span>
						<span class="doc">The datetime format givent to `|localizeddate` twig filter</span>
					</li>
					<li>
						<span class="code">number_format:</span>
						<span class="doc"></span>
						<ul>
							<li>
								<span class="code">decimal: <span class="default_value">0</span> <span class="accepted_values">int</span></span>
								<span class="doc">The number of decimal for the twig number format</span>
							<li>
							<li>
								<span class="code">decimal_point: <span class="default_value">.</span> <span class="accepted_values">string</span></span>
								<span class="doc">The decimal separator for the twig number format</span>
							<li>
							<li>
								<span class="code">thousand_separator: <span class="default_value">,</span> <span class="accepted_values">string</span></span>
								<span class="doc">The thousand separator for the twig number format</span>
							<li>
						</ul>
					</li>
				</ul>
			</li>
			<li>
				<span class="code">templates_dirs: <span class="default_value">[]</span> <span class="accepted_values">array</span></span>
				<span class="doc">Array of template path, the templates will be used to create the generated code</span>
			</li>
			<li>
				<span class="code">stylesheets: <span class="default_value">[]</span> <span class="accepted_values">array</span></span>
				<span class="doc">Array of stylesheets you want to add in your theme for all your admin pages</span>
				<ul>
					<li>
						<span class="code">- { path: bundles/mybundle/css/print.css, media: print }<span class="accepted_values">array</span></span>
						<span class="doc">Key path is required and media is default <span class="default_value">all</span></span>
					</li>
				</ul>
			</li>
			<li>
				<span class="code">javascripts: <span class="default_value">[]</span> <span class="accepted_values">array</span></span>
				<span class="doc">Array of javascripts you want to add in your theme for all your admin pages</span>
				<ul>
					<li>
						<span class="code">- { path: bundles/mybundle/js/common.js }<span class="accepted_values">array</span></span>
						<span class="doc">Key path is required</span>
					</li>
					<li>
						<span class="code">- { route: fos_js_routing_js, routeparams: { callback: "fos.Router.setData" } }<span class="accepted_values">array</span></span>
						<span class="doc">Key route is required, and routeparams default is <span class="default_value">{}</span> </span>
					</li>
				</ul>
			</li>
		</ul>
	</li>
</ul>
