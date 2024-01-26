---
aliases: /handbook/engineering/infrastructure/team/scalability/observability/capacity_planning.html

title: "Capacity Planning"
---

We maintain and improve the Capacity Planning process that is described [in the Infrastructure Handbook](/handbook/engineering/infrastructure/capacity-planning/). This is a controlled activity covered by SOC 2. Please see [this issue](https://gitlab.com/gitlab-com/gl-security/security-assurance/security-compliance-commercial-and-dedicated/sec-compliance/observation-management/-/issues/604) for further details

The goal of this process is to predict and prevent saturation incidents on GitLab.com.

Issues are kept in the [capacity planning issue tracker](https://gitlab.com/gitlab-com/gl-infra/capacity-planning-trackers/gitlab-com/-/issues). Where an issue is needed to improve metrics to support this process, we raise an issue in the [Scalability group tracker](https://gitlab.com/gitlab-com/gl-infra/scalability/-/issues) with the label of `Saturation Metrics`.

Please see [Tamland](./tamland.html) for more information on the forecasting tool we develop and use.

## Triage Duties

The triage duties are:
1. Review the [handover issue](https://gitlab.com/gitlab-com/gl-infra/capacity-planning/-/issues/?sort=created_date&state=opened&label_name%5B%5D=Handover&first_page_size=20) and close it when you're ready to get started with triage
1. Review all capacity planning issues that are past their due date, or in the Open column (which means they do not have a `capacity-planning::` workflow label). The [saturation labels](/handbook/engineering/infrastructure/capacity-planning/#saturation-labels) can help in choosing which issues to review first, if there are many with the same due date.
1. For each item, check if the warning still applies and follow up with the DRI or other engineers for an updated status.
1. Set appropriate due dates for the next review.
1. Raise any significant concerns through the [SaaS Availability weekly standup](/handbook/engineering/#saas-availability-weekly-standup)(currently on Tuesdays in UTC afternoon) by adding them to the [meeting agenda](https://docs.google.com/document/d/1Zk3qgbn8iDyJRq0i5C5LPBgEopY6o1tpYEKfdNfA9Bg/edit#).
   * An issue is a significant concern if it is a critical non-horizontally-scalable resource at risk of imminent saturation or an issue that needs additional attention from leadership.
   * If something is really pressing, please raise significant concerns with the Engineering Manager who will escalate to leadership as appropriate.
1. Check that Tamland is running and generating output and bring this to the team's attention if it is not running. Check the [scheduled pipelines on ops](https://ops.gitlab.net/gitlab-com/gl-infra/tamland/-/pipelines?page=1&scope=all&source=schedule) for this. There should be a daily job populating the cache, and a weekly job for tamland without failures.
1. Create a [handover issue](https://gitlab.com/gitlab-com/gl-infra/capacity-planning/-/issues/new?issuable_template=Handover&issue[title]=Triage%20handover%20notes%20YYYY-MM-DD) once your shift comes to an end and hand information over to the next person taking it.

Make sure to set aside at least half a work day during each week in your rotation to go through the items in the Capacity Planning board.
Consider re-scheduling one of your shifts if it coincides with another rotation (e.g. EOC on-call duties).
When your rotation is finished, you need to provide handover notes in the #infra_capacity-planning channel for the incoming person.

Some tips to help you to get started on duties:
1. For items that need to be monitored further, it is encouraged to attach the current forecast in the comment as the forecast would change over the following weeks and we wouldn't be able to see the previous forecasts.
1. Assign the issue to the Engineering Manager for the team that owns the service.
1. Oftentimes, you might want to query the underlying query of the saturation component in order to get more context of the current state. You could either:
   * Follow the Grafana alert dashboard, copy over the query from the Explore page, and experiment with it in Thanos.
   * Search for `component: <component_name>` (e.g. `component: disk_space`) in `runbooks` project, the underlying recording rule can be found in `rules/autogenerated-saturation.yml` ([example for `component: disk_space`](https://gitlab.com/gitlab-com/runbooks/-/blob/cf83fdff44a0d5828a5343d2242dbd49eefdaf08/rules/autogenerated-saturation.yml#L108))
1. Looking for the component / alert name in the [Capacity Planning Issue Tracker](https://gitlab.com/gitlab-com/gl-infra/capacity-planning/-/issues)
   can be a good source of information, as some recurring saturation forecast share the same or similar causes, or just to gain some insight into how
   these issues have been investigated in the past.
1. Some events can impact negatively the accuracy of Tamland's forecast. For example, infrastructure changes can change the baseline for a saturation metric.
   Or a one-off usage spike can skew the forecast overly pessimistic. If you suspect one of these situations is causing unwarranted saturation alerts,
   you can try adding `trend_changepoints` and `ignore_outliers` entries to the [forecast parameters](https://gitlab.com/gitlab-com/gl-infra/tamland/-/blob/main/forecast_params.yml).
   For more details, see [Tuning the forecast](https://gitlab.com/gitlab-com/gl-infra/tamland/-/blob/main/README.md#tuning-the-forecast).
1. Sometimes Tamland may generate alerts for services whose saturation forcast is generally trending downwards, but for which Tamland's confidence interval
   (the light blue area in prediction graphs) may still include the possibility of saturation. If your investigation yields no reason to suspect the saturation
   risk is real, you can opt for tagging the issue as ~capacity-planning::monitor and moving its due date one week or more.