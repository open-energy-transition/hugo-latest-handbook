{{- /*  Initialize. */}}
{{- $section_group := "" }}

{{- /* Get params. */}}
{{- with (.Get 0) }}
  {{- $section_group = . }}
{{- else }}
  {{- errorf "The %q shortcode requires a single positional argument for section_group."}}
{{- end }}

{{- $foundMemberDict := dict }}
{{- $beTeamDict := dict }}
{{- $feTeamDict := dict }}
{{- $uxTeamDict := dict }}
{{- $pmData := slice }}
{{- $emData := slice }}
{{- $femData := slice }}

{{- $stages := partials.IncludeCached "data/stages" . }}
{{- $teamMembers := partials.IncludeCached "data/team-by-gitlab" . }}

{{- range $stages }}
  {{- range .groups }}
    {{- if eq .name $section_group }}
      {{- $be_team_tag := .be_team_tag }}
      {{- $fe_team_tag := .fe_team_tag }}
      {{- $pm := .pm }}
      {{- $ux := .ux }}
      {{- $em := .backend_engineering_manager }}
      {{- $fem := .frontend_engineering_manager }}
      
      {{- range $k, $v := $teamMembers }}
        {{- if in .departments $be_team_tag }}
          {{- if not (eq (lower .name) (lower $em)) }}
            {{- $beTeamDict = merge $beTeamDict (dict (lower .gitlab) . ) }}
            {{- $foundMemberDict = merge $foundMemberDict (dict (lower .gitlab) . ) }}
          {{- end }}
        {{- end }}
        {{- if in .departments $fe_team_tag }}
          {{- if not (eq (lower .name) (lower $fem)) }}
            {{- $feTeamDict = merge $feTeamDict (dict (lower .gitlab) . ) }}
            {{- $foundMemberDict = merge $foundMemberDict (dict (lower .gitlab) . ) }}
          {{- end }}
        {{- end }}
        {{- if eq (lower .name) (lower $pm) }}
          {{- $pmData = append . $pmData }}
          {{- $foundMemberDict = merge $foundMemberDict (dict (lower .gitlab) . ) }}
        {{- end }}
        {{- if eq (lower .name) (lower $em) }}
          {{- $emData = append . $emData }}
          {{- $foundMemberDict = merge $foundMemberDict (dict (lower .gitlab) . ) }}
        {{- end }}
        {{- if and (eq (lower .name) (lower $fem)) (not (eq $fem $em)) }}
          {{- $femData = append . $femData }}
          {{- $foundMemberDict = merge $foundMemberDict (dict (lower .gitlab) . ) }}
        {{- end }}
        {{- if in $ux .name }}
          {{- $uxTeamDict = merge $uxTeamDict (dict (lower .gitlab) . ) }}
          {{- $foundMemberDict = merge $foundMemberDict (dict (lower .gitlab) . ) }}
        {{ end }}
      {{ end }}
    {{ end }}
  {{- end }}
{{- end }}
#### {{$section_group}}

<table>
  <thead>
    <tr>
      <th>Type</th>
      <th>Names</th>
      <th>Count</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th><abbr title="Product Manager">PM</abbr></th>
      <td>{{- with (index $pmData 0) }}{{ partial "member" . }}{{- end }}
      </td>
      <td>{{ len $pmData }}</td>
    </tr>
    <tr>
      <th><abbr title="User Research">UX</abbr></th>
      <td>{{- if gt (len $uxTeamDict) 0}}
          {{- range $uxTeamDict }}
            {{ partial "member" . }}
          {{- end }}
        {{- end }}</td>
      <td>{{ len $uxTeamDict }}</td>
    </tr>
    <tr>
      <th><abbr title="Engineering Manager">EM</abbr></th>
      <td>{{- with (index $emData 0) }}{{ partial "member" . }}{{- end }}</td>
      <td>{{ len $emData }}</td>
    </tr>
    <tr>
      <th><abbr title="Frontend Engineering Manager">FEM</abbr></th>
      <td>{{- with (index $femData 0) }}{{ partial "member" . }}{{- end }}</td>
      <td>{{ len $femData }}</td>
    </tr>
    <tr>
      <th><abbr title="Frontend">FE</abbr></th>
      <td>{{- if gt (len $feTeamDict) 0}}
            {{- range $feTeamDict }}
              {{ partial "member" . }}
            {{- end }}
          {{- end }}</td>
      <td>{{ len $feTeamDict }}</td>
    </tr>
    <tr>
      <th><abbr title="Backend">BE</abbr></th>
      <td>{{- if gt (len $beTeamDict) 0 }}
            {{- range $beTeamDict }}
              {{ partial "member" . }}
            {{- end }}
          {{- end }}</td>
      <td>{{ len $beTeamDict }}</td>
    </tr>
    <tr>
      <th>Total</th>
      <td></td>
      <td>{{ len $foundMemberDict }}</td>
    </tr>
  </tbody>
</table>

<style>
    img.avatar {
    width: 30px;
    height: 30px;
    max-width: 30px;
    max-height: 30px;
    overflow: hidden;
    margin-right: 10px;
    border-radius: 50%;
    border: 1px solid lightgray;
    aspect-ratio: auto 90 / 90;
    overflow-clip-margin: content-box;
    }
</style>